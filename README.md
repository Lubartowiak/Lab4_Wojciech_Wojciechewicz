Lab4_Wojciech_Wojciechewicz

# 1. Utworzenie pliku manifestu YAML
nano loop.yaml

# 2. Wklejenie definicji Poda
```
apiVersion: v1
kind: Pod
metadata:
  name: loop
spec:
  restartPolicy: Never
  containers:
  - name: busybox
    image: busybox:1.36.1
    command: ["sh", "-c", "for i in {1..5}; do echo \"$i - A piece of cake !\"; done"]
```
# 3. Utworzenie Poda na podstawie manifestu
kubectl apply -f loop.yaml

# 4. Sprawdzenie statusu wszystkich Podów
kubectl get pods

# 5. Podgląd szczegółowych informacji o Podzie loop
kubectl describe pod loop

# 6. Wyświetlenie logów
kubectl logs loop

# 7. Usunięcie starego Poda
kubectl delete pod loop

# 8. Edycja manifestu (dodanie "sleep infinity" do komendy)
nano loop.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: loop
spec:
  containers:
  - name: busybox
    image: busybox:1.36.1
    command: ["sh", "-c", "for i in {1..5}; do echo \"$i - A piece of cake !\"; done; sleep infinity"]

```
# 9. Ponowne utworzenie Poda po modyfikacji
kubectl apply -f loop.yaml

# 10. Sprawdzenie statusu po zmianach
kubectl get pods

# 11. Wyświetlenie logów
kubectl logs loop
