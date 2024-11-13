# Flashage d'une ESP32-C6 via le terminal

Ce guide vous montre comment effacer la mémoire et flasher un firmware sur une carte ESP32-C6 en utilisant l'outil `esptool`.

### Prérequis

- **esptool** : Assurez-vous que `esptool` est installé. Pour l'installer via `pip`, utilisez :
  ```bash
  pip install esptool
  ```
- **Firmware** : Assurez-vous d'avoir le fichier firmware à flasher sur votre ESP32-C6.

### Instructions
1. **Identifier le port** : Connectez votre ESP32-C6 à votre ordinateur et identifiez le port de connexion. Par exemple, sur Linux/MacOS, cela pourrait être `/dev/ttyUSB0`, et sur Windows, `COM3`.

2. **Effacer la mémoire de la carte** :  
   Dans un terminal, exécutez la commande suivante pour effacer la mémoire de l'ESP32-C6 :

   ```bash
   esptool --chip esp32c6 --port [votre port] erase_flash
   ```
3. **Flasher le firmware** : 
   Une fois la mémoire effacée, flashez le firmware sur la carte avec la commande suivante :

   ```bash
   esptool --chip esp32c6 --port [votre port] --baud 460800 write_flash -z 0x0 [le firmware]
   ```
   - Remplacez [votre port] par le port de votre ESP32-C6.
   - Remplacez [le firmware] par le chemin vers le fichier firmware (ex: esp32c6-20241023-v1.24.0-preview.462.g078ead24f.bin)

### Exemple complet
   ```bash
   esptool --chip esp32c6 --port COM15 erase_flash
   esptool --chip esp32c6 --port COM15 --baud 460800 write_flash -z 0x0 esp32c6-20241023-v1.24.0-preview.462.g078ead24f.bin
   ```
