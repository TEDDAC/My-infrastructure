```bash
helm show values ananace-charts/funkwhale > .\values.yaml

helm install funkwhale ananace-charts/funkwhale -f .\values.yaml

helm upgrade funkwhale ananace-charts/funkwhale -f .\values.yaml

/venv/bin/funkwhale-manage fw users create --superuser
```

Je crois ne pas avoir assez de puissance, les pods redémarre h24 XD