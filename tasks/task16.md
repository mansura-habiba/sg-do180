Description
---
- use json file to create a temaplate
- process template to see the parameter
- create application from template 


# use json file to create a temaplate
```
oc create -f <filename>.json
```

## Example 
```
oc create -f quote-php-template.json
```

## check 

```
oc get temaplates
```

# process template to see the parameter

```
oc preocess --parameter <template name>
```

# Create app 

```
oc process <template name> -p param1=value1 -p param2=value2 | oc create -f -
```

OR 

```
oc new-app --template=<templale name> -p param1=value1   -p param2=value2 --as-deployment-config
```

## Check 

```
oc get pods
```

# Expose service 

```
oc expose service/<service name >
```

## check route

```
oc get routes
```
