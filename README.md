# toast-hawai-fetzt-helm-eher-nicht

## Szenario 1 (Chart nicht installiert)

1) Start mit `helm upgrade --install foo chart/ --set datahub.enabled=true`
```yaml
DATAHUB_REVISION: FIRST
SOMETHING_ELSE: ELSE
DATAHUB_REVISION: SECOND
```
2) Dann `helm upgrade --install foo chart/ --set datahub.enabled=false`
```yaml
SOMETHING_ELSE: ELSE
```
3) Dann `helm upgrade --install foo chart/ --set datahub.enabled=true`
```yaml
DATAHUB_REVISION:  FIRST                                                                                                                                                                                                                              
SOMETHING_ELSE:    ELSE
```
 
Geht immer so weiter ...

## Szenario 2 (Chart nicht installiert)

1) Start deploy mit `helm upgrade --install foo chart/ --set datahub.enabled=false`
```yaml
SOMETHING_ELSE:  ELSE
DATAHUB_REVISION:  SECOND
```
2) Dann `helm upgrade --install foo chart/ --set datahub.enabled=true`
```yaml
DATAHUB_REVISION:  FIRST                                                                                                                                                                                                                              
SOMETHING_ELSE:    ELSE
```
3) Dann `helm upgrade --install foo chart/ --set datahub.enabled=false`
```yaml
SOMETHING_ELSE:  ELSE
```
4) Dann `helm upgrade --install foo chart/ --set datahub.enabled=true`
```yaml
DATAHUB_REVISION:  FIRST
SOMETHING_ELSE:    ELSE
``` 

Geht immer so weiter ...
 