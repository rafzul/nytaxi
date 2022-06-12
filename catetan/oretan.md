28 Mei 2022 
- Goals: 
  pengin task **bashoperator** yang jalan di celeryworkers nyimpen data ke harddisk local
- Platform/environment
  - Kubernetes: pake k3s via k3d
  - Airflow: airflow **helm** chart
- Current Solution: pake **local-path-provisioner** yang disediain k3s langsung buat nyambungin harddisk -> folder di nodes -> folder di worker pods
- Langkah yang udh dilakuin: 
  - setup local-path-provisioner di /media/rafzul/terminal_dogma1/nytaxidata/:/storage
  - change configMap biar folder kebaca
  - setup PVC 
  - setup extraVolume pake https://github.com/airflow-helm/charts/blob/main/charts/airflow/docs/faq/kubernetes/mount-persistent-volumes.md
- kondisi
  - PVC kebaca dan kepake
  - /storage kebaca di kubernetes nodes
  - isi hardisk yg disambungin ke /storage kebaca di kubernetes nodes
  - *extraVolumeMounts mountPath nya ngga kebuat di dalem worker pods*

List of hypotesis and solutions:
- configmapnya local-path-provisioner ngga keset buat baca selain di   default place
    - solutions 1: di k3d cluster create, volumenya ganti ke default
      - defaultnya pake yg /var/lib/rancher/k3s/storage ato /opt/local-path-provisioner??? --> coba 22nya, yg kebaca yg mana
    - solutions 2: ubah default folder
      - gak disarankan, ngubah banyak

- 
  - 