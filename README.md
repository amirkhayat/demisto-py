# Demisto SDK for Python

A Python library for the Demisto API.

## Usage

```python
import demisto
client = demisto.DemistoClient('admin', 'password', 'https://localhost:8443')
client.Login()
```
Should return <Response [200]>


You can create incidents:

```python
client.CreateIncident('incident-name', 'incident-type', 0, 'owner', [{"type": "label", "value": "demisto"}], 'details', {"alertsource":"demisto"})

```

You can search for incidents by filter:

```python
client.SearchIncidents(0,100,'')
```

Will return all incidents, with a max limit of 100 incidents to return, and page 0 of it

A bit more complex search:

```python
client.SearchIncidents(0,100,'name:test')
```

Will return incidents with name test

* Note - on macOS, the system OpenSSL does not supprot TLSv12 which Demisto server mandates. To run the examples on macOS you will need to install brew and then OpenSSL and Python via brew.

If you don't have brew installed:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

To install Python with new OpenSSL support:
```
brew update
brew install openssl
brew install python --with-brewed-openssl
```

To run the examples:
```
/usr/local/Cellar/python/2.7.13/bin/python example -param val -param val
```
