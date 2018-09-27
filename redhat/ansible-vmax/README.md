Se muestran ejemplos de solicitudes de llamadas HTTP a REST Api para difrerntes metodos

Ansible-VMax
Integraciones de los playbooks para integraciones Ansible y VMax

# ....::::Metodos::::....

# VALIDATION VMAX ID
Se valida el id del VMax este metodo nos sirve para verificar si VMax se encuentra disponible

curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIDATION VMAX ID
OUTPUT:
{
    "symmetrixId": [
        "000197000564"
    ],
    "num_of_symmetrix_arrays": 1,
    "success": true
}

# VALIDATION ENDPOINT
Se valida que el api se encuentre disponible y que pueda responder llamadas.
 curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/system/version' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIDATION ENDPOINT
  OUTPUT:
  {
    "version": "V8.4.0.18"
}
  
# VALIDATION VMAX Storage Resorce Pool NAME
Se verifica que el Storage resource pool indicado exista.
curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/84/sloprovisioning/symmetrix/{{vmax3_sn}}/srp' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='


# OUTPUT VALIDATION VMAX Storage Resorce Pool NAME
OUTPUT:
  {
    "srpId": [
        "SRP_1"
    ]
}

# VALIDATION Storage Resorce Pool FREE SPACE
Se verifica que el Storage resource pool indicado tenga espacio disponible.
curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/srp/{{srp_vmax3}}' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIDATION Storage Resorce Pool FREE SPACE
 OUTPUT:
 {
    "srp": [
        {
            "srpId": "SRP_1",
            "num_of_disk_groups": 1,
            "description": "",
            "emulation": "FBA",
            "reserved_cap_percent": 10,
            "total_usable_cap_gb": 637528.6,
            "total_subscribed_cap_gb": 693900.74,
            "total_allocated_cap_gb": 292601.4,
            "total_snapshot_allocated_cap_gb": 5807,
            "total_srdf_dse_allocated_cap_gb": 0,
            "rdfa_dse": true,
            "num_of_srp_slo_demands": 2,
            "num_of_srp_sg_demands": 1,
            "diskGroupId": [
                "1"
            ],
            "srpSgDemandId": [
                "SLO_sg"
            ],
            "srpSloDemandId": [
                "Diamond",
                "None"
            ]
        }
    ],
    "success": true
}


# VALIADTION STORAGE GROUP
Se valida el que el storage pool exista.
 curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIADTION STORAGE GROUP
  OUTPUT:  
{
    "storageGroup": [
        {
            "storageGroupId": "ESX_Linux_Dev_sg",
            "slo": "None",
            "srp": "None",
            "workload": "NONE",
            "slo_compliance": "NONE",
            "num_of_vols": 14,
            "num_of_child_sgs": 0,
            "num_of_parent_sgs": 0,
            "num_of_masking_views": 1,
            "num_of_snapshots": 0,
            "cap_gb": 20480.27,
            "device_emulation": "FBA",
            "type": "Standalone",
            "child_storage_group": [],
            "parent_storage_group": [],
            "maskingview": [
                "ESX_Linux_Dev_mv"
            ]
        }
    ],
    "success": true
}
  

# VALIDATION EXISTENT LUNS AND IDS
Se validan las LUNs y Ids
 curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/maskingview/{{maskingview}}/connections' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIDATION EXISTENT LUNS AND IDS
  OUTPUT:
  {
    "num_of_connections": 2240,
    "maskingViewConnection": [
        {
            "volumeId": "00583",
            "host_lun_address": "0005",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b016e",
            "alias": "vwoaahxp145/h5",
            "dir_port": "FA-2D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00584",
            "host_lun_address": "0006",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b014e",
            "alias": "vwoaahxp143/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00584",
            "host_lun_address": "0006",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50a014e",
            "alias": "vwoaahxp159/h4",
            "dir_port": "FA-4D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00585",
            "host_lun_address": "0007",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b017e",
            "alias": "vwoaahxp144/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00585",
            "host_lun_address": "0007",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50a013e",
            "alias": "vwoaahxp160/h4",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00587",
            "host_lun_address": "0008",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b018e",
            "alias": "vwoaahxp139/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00587",
            "host_lun_address": "0008",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50a01bd",
            "alias": "vwoaahxp174/h2",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00745",
            "host_lun_address": "0000",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01005837d",
            "alias": "vwoaahxp174/h3",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00745",
            "host_lun_address": "0000",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50a010f",
            "alias": "vwoaahxp141/h2",
            "dir_port": "FA-2D:25",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00746",
            "host_lun_address": "0001",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01ad",
            "alias": "vwoaahxp176/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00746",
            "host_lun_address": "0001",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b018d",
            "alias": "vwoaahxp173/h3",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b018d",
            "alias": "vwoaahxp173/h3",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b015e",
            "alias": "vwoaahxp142/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00747",
            "host_lun_address": "0002",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013e",
            "alias": "vwoaahxp140/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00747",
            "host_lun_address": "0002",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013b",
            "alias": "vwoaahxp182/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00747",
            "host_lun_address": "0002",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01fe",
            "alias": "vwoaahxp159/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50a011f",
            "alias": "vwoaahxp140/h2",
            "dir_port": "FA-5D:25",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013e",
            "alias": "vwoaahxp140/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00749",
            "host_lun_address": "0004",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b012e",
            "alias": "vwoaahxp141/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00749",
            "host_lun_address": "0004",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01fe",
            "alias": "vwoaahxp159/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b01fe",
            "alias": "vwoaahxp159/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50a013f",
            "alias": "vwoaahxp142/h2",
            "dir_port": "FA-2D:25",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b015e",
            "alias": "vwoaahxp142/h5",
            "dir_port": "FA-2D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50a016f",
            "alias": "vwoaahxp139/h2",
            "dir_port": "FA-4D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b018e",
            "alias": "vwoaahxp139/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2B",
            "host_lun_address": "000A",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b013e",
            "alias": "vwoaahxp140/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2B",
            "host_lun_address": "000A",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b01dc",
            "alias": "vwoaahxp180/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D39",
            "host_lun_address": "000B",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013b",
            "alias": "vwoaahxp182/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D39",
            "host_lun_address": "000B",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50a015c",
            "alias": "vwoaahxp180/h4",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D55",
            "host_lun_address": "000C",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b012e",
            "alias": "vwoaahxp141/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D55",
            "host_lun_address": "000C",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b016e",
            "alias": "vwoaahxp145/h5",
            "dir_port": "FA-2D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00ED7",
            "host_lun_address": "000D",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50a010f",
            "alias": "vwoaahxp141/h2",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00ED7",
            "host_lun_address": "000D",GROUP
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b012e",
            "alias": "vwoaahxp141/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        }
    ],
    "success": true
}

# Realizar el filtrado, de los volumeId encontrados
Ejemplo:
AFTER FILTERING LIST1:
            "volumeId": "00583",
            "volumeId": "00584",
            "volumeId": "00585",
            "volumeId": "00587",
            "volumeId": "00745",
            "volumeId": "00746",
            "volumeId": "00747",
            "volumeId": "00748",
            "volumeId": "00749",
            "volumeId": "00D2A",
            "volumeId": "00D2B",
            "volumeId": "00D39",
            "volumeId": "00D55",
            "volumeId": "00ED7",

# EXECUTION CREATION OF LUNS
Crear una nueva LUN
curl -X PUT \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}' \
  -H 'Content-Type: application/json' \
  -d '{
  "editStorageGroupActionParam": {
    "expandStorageGroupParam": {
      "num_of_vols": 1,
      "volumeAttribute": {
        "volume_size": "2",
        "capacityUnit": "TB"
      }
    }
  }
} 

# OUTPUT EXECUTION CREATION OF LUNS
Salida correcta de la creación de la lun
OUTPUT:
{
    "success": true
}

# VALIDATION AFTER LUN CREATION:
Se valida posterior a la creación de la lun para comparar las salidas
curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/maskingview/{{maskingview}}/connections' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIDATION AFTER LUN CREATION:  
OUTPUT:
{
    "num_of_connections": 2400,
    "maskingViewConnection": [
        {
            "volumeId": "00583",
            "host_lun_address": "0005",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b016e",
            "alias": "vwoaahxp145/h5",
            "dir_port": "FA-2D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00584",
            "host_lun_address": "0006",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b014e",
            "alias": "vwoaahxp143/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00584",
            "host_lun_address": "0006",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50a014e",
            "alias": "vwoaahxp159/h4",
            "dir_port": "FA-4D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00585",
            "host_lun_address": "0007",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b017e",
            "alias": "vwoaahxp144/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00585",
            "host_lun_address": "0007",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50a013e",
            "alias": "vwoaahxp160/h4",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00587",
            "host_lun_address": "0008",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50b018e",
            "alias": "vwoaahxp139/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00587",
            "host_lun_address": "0008",
            "cap_gb": "0.01",
            "initiatorId": "20000025b50a01bd",
            "alias": "vwoaahxp174/h2",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00745",
            "host_lun_address": "0000",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01005837d",
            "alias": "vwoaahxp174/h3",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00745",
            "host_lun_address": "0000",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50a010f",
            "alias": "vwoaahxp141/h2",
            "dir_port": "FA-2D:25",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00746",
            "host_lun_address": "0001",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01ad",
            "alias": "vwoaahxp176/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00746",
            "host_lun_address": "0001",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b018d",
            "alias": "vwoaahxp173/h3",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b018d",
            "alias": "vwoaahxp173/h3",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b015e",
            "alias": "vwoaahxp142/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00747",
            "host_lun_address": "0002",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013e",
            "alias": "vwoaahxp140/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00747",
            "host_lun_address": "0002",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013b",
            "alias": "vwoaahxp182/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00747",
            "host_lun_address": "0002",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01fe",
            "alias": "vwoaahxp159/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50a011f",
            "alias": "vwoaahxp140/h2",
            "dir_port": "FA-5D:25",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00748",
            "host_lun_address": "0003",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013e",
            "alias": "vwoaahxp140/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00749",
            "host_lun_address": "0004",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b012e",
            "alias": "vwoaahxp141/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00749",
            "host_lun_address": "0004",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b01fe",
            "alias": "vwoaahxp159/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b01fe",
            "alias": "vwoaahxp159/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50a013f",
            "alias": "vwoaahxp142/h2",
            "dir_port": "FA-2D:25",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b015e",
            "alias": "vwoaahxp142/h5",
            "dir_port": "FA-2D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50a016f",
            "alias": "vwoaahxp139/h2",
            "dir_port": "FA-4D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D2A",
            "host_lun_address": "0009",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b018e",
            "alias": "vwoaahxp139/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2B",
            "host_lun_address": "000A",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b013e",
            "alias": "vwoaahxp140/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D2B",
            "host_lun_address": "000A",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b01dc",
            "alias": "vwoaahxp180/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D39",
            "host_lun_address": "000B",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50b013b",
            "alias": "vwoaahxp182/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D39",
            "host_lun_address": "000B",
            "cap_gb": "2048.02",
            "initiatorId": "20000025b50a015c",
            "alias": "vwoaahxp180/h4",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00D55",
            "host_lun_address": "000C",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b012e",
            "alias": "vwoaahxp141/h5",
            "dir_port": "FA-4D:24",
            "logged_in": false,
            "on_fabric": false
        },
        {
            "volumeId": "00D55",
            "host_lun_address": "000C",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b016e",
            "alias": "vwoaahxp145/h5",
            "dir_port": "FA-2D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00ED7",
            "host_lun_address": "000D",
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50a010f",
            "alias": "vwoaahxp141/h2",
            "dir_port": "FA-1D:24",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "00ED7",
            "host_lun_address": "000D",GROUP
            "cap_gb": "2048.03",
            "initiatorId": "20000025b50b012e",
            "alias": "vwoaahxp141/h5",
            "dir_port": "FA-1D:24",
            "logged_in": false,
            "on_fabric": false
        }
        {
            "volumeId": "010C1",
            "host_lun_address": "000E",
            "cap_gb": "2048.0",
            "initiatorId": "20000025b50b010c",
            "alias": "vwoaahxp179/h5",
            "dir_port": "FA-5D:25",
            "logged_in": true,
            "on_fabric": true
        },
        {
            "volumeId": "010C1",
            "host_lun_address": "000E",
            "cap_gb": "2048.0",
            "initiatorId": "20000025b50a019b",
            "alias": "vwoaahxp182/h4",
            "dir_port": "FA-5D:25",
            "logged_in": false,
            "on_fabric": false
        }
    ],
    "success": true
}

# AFTER FILTERING AND COMPARING
Se filtra y se compara con el arreglo de Luns de la validación previa a la creación
            "volumeId": "010C1",
            "volumeId": "00ED7",
            "volumeId": "00D55",
            "volumeId": "00D39",
            "volumeId": "00D2B",
            "volumeId": "00D2A",
            "volumeId": "00749",
            "volumeId": "00748",
            "volumeId": "00747",
            "volumeId": "00746",
            "volumeId": "00745",
            "volumeId": "00587",
            "volumeId": "00585",
            "volumeId": "00584",
            "volumeId": "00583",

De lo cual obtenemos que la nueva LUN es: [volumeId: 010C1]


# VALIDATION NEW VOLUME
Se realiza la petición para validar el nuevo columen y obtener su VMWareId
curl -X GET \
  'https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/010C1' \
  -H 'Authorization: Basic dm5kcnRzYXA6QzBubmVjdHJpeA=='

# OUTPUT VALIDATION NEW VOLUME
OUTPUT:
{
    "volume": [
        {
            "volumeId": "010C1",
            "type": "TDEV",
            "emulation": "FBA",
            "ssid": "FFFFFFFF",
            "allocated_percent": 0,
            "cap_gb": 2048,
            "cap_mb": 2097154,
            "cap_cyl": 1118482,
            "status": "Ready",
            "reserved": false,
            "pinned": false,
            "physical_name": "",
            "volume_identifier": "N/A",
            "wwn": "60000970000197000564533031304331",
            "encapsulated": false,
            "num_of_storage_groups": 1,
            "num_of_front_end_paths": 4,
            "storageGroupId": [
                "ESX_Linux_Dev_sg"
            ],
            "symmetrixPortKey": [
                {
                    "directorId": "FA-1D",
                    "portId": "24"
                },
                {
                    "directorId": "FA-2D",
                    "portId": "25"
                },
                {
                    "directorId": "FA-4D",
                    "portId": "24"
                },
                {
                    "directorId": "FA-5D",
                    "portId": "25"
                }
            ]
        }
    ],
    "success": true
}

# WITH FILTER:
Se obtiene el wwn
            "wwn": "60000970000197000564533031304331",


# CREACION DE MASKING VIEW

{
	"info": {
		"_postman_id": "5f0b1b05-6f71-4852-a00d-8e5a4fd18d3c",
		"name": "VMAX3",
		"description": "VMAX3 collection of provisioning and monitoring API calls.",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
	},
	"item": [
		{
			"name": "a.1 Provisioning DS",
			"description": "Process to provision storage to an already generated host",
			"item": [
				{
					"name": "Validation IP/Endpoint",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/system/version",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"system",
								"version"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation VMAX3 SRP",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/84/sloprovisioning/symmetrix/{{vmax3_sn}}/srp",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"84",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"srp"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation VMAX3 SRP available space",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/srp/{{srp_vmax3}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"srp",
								"{{srp_vmax3}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation Storage Group",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"storagegroup",
								"{{storagegroup}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate Masking View Connections",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/maskingview/{{maskingview}}/connections",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"maskingview",
								"{{maskingview}}",
								"connections"
							]
						}
					},
					"response": []
				},
				{
					"name": "Execution LUN creation/assignment",
					"request": {
						"method": "PUT",
						"header": [
							{
								"key": "Content-Type",
								"value": "application/json"
							}
						],
						"body": {
							"mode": "raw",
							"raw": "{\r\n  \"editStorageGroupActionParam\": {\r\n    \"expandStorageGroupParam\": {\r\n      \"num_of_vols\": 1,\r\n      \"volumeAttribute\": {\r\n        \"volume_size\": \"2\",\r\n        \"capacityUnit\": \"TB\"\r\n      }\r\n    }\r\n  }\r\n} \r\n"
						},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"storagegroup",
								"{{storagegroup}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate LUN Creation",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/maskingview/{{maskingview}}/connections",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"maskingview",
								"{{maskingview}}",
								"connections"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate LUN Configuration",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/00CF9",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"00CF9"
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "a.2 Provisioning RDM",
			"description": "",
			"item": [
				{
					"name": "Validate LUN",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/{{lunid}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"{{lunid}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation IP/Endpoint",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/system/version",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"system",
								"version"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation VMAX3 SRP",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/84/sloprovisioning/symmetrix/{{vmax3_sn}}/srp",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"84",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"srp"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation VMAX3 SRP available space",
					"event": [
						{
							"listen": "prerequest",
							"script": {
								"id": "10794664-e9c4-4f64-bad3-e7f1ec0f30df",
								"type": "text/javascript",
								"exec": [
									""
								]
							}
						}
					],
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/srp/{{srp_vmax3}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"srp",
								"{{srp_vmax3}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate Masking View Connections",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/maskingview/{{maskingview}}/connections",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"maskingview",
								"{{maskingview}}",
								"connections"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate Storage Group",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"storagegroup",
								"{{storagegroup}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Execution LUN creation/assignment",
					"request": {
						"method": "PUT",
						"header": [
							{
								"key": "Content-Type",
								"value": "application/json"
							}
						],
						"body": {
							"mode": "raw",
							"raw": "{\r\n  \"editStorageGroupActionParam\": {\r\n    \"expandStorageGroupParam\": {\r\n      \"num_of_vols\": 2,\r\n      \"volumeAttribute\": {\r\n        \"volume_size\": \"100\",\r\n        \"capacityUnit\": \"GB\"\r\n      }\r\n    }\r\n  }\r\n} \r\n"
						},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"storagegroup",
								"{{storagegroup}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate LUN Creation",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/maskingview/{{maskingview}}/connections",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"maskingview",
								"{{maskingview}}",
								"connections"
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "a.3 Reclaim device",
			"description": "",
			"item": [
				{
					"name": "Validation IP/Endpoint",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/system/version",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"system",
								"version"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation LUN exists",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/{{lunid}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"{{lunid}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Execute LUN unmap",
					"request": {
						"method": "PUT",
						"header": [
							{
								"key": "Content-Type",
								"value": "application/json"
							}
						],
						"body": {
							"mode": "raw",
							"raw": "{\r\n  \"editStorageGroupActionParam\": {\r\n    \"removeVolumeParam\": {\r\n      \"volumeId\": [\r\n        \"0074F\"\r\n      ]\r\n    }\r\n  }\r\n}\r\n"
						},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"storagegroup",
								"{{storagegroup}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation LUN unmapped",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/{{lunid}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"{{lunid}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation LUN unmapped 1 week later",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/0074F",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"0074F"
							]
						}
					},
					"response": []
				},
				{
					"name": "Execution free LUN",
					"request": {
						"method": "PUT",
						"header": [
							{
								"key": "Content-Type",
								"value": "application/json"
							}
						],
						"body": {
							"mode": "raw",
							"raw": "{\r\n  \"editVolumeActionParam\": {\r\n    \"freeVolumeParam\": {\r\n      \"free_volume\": true\r\n    }\r\n  }\r\n} \r\n"
						},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/84/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/0074F",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"84",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"0074F"
							]
						}
					},
					"response": []
				},
				{
					"name": "Execution delete LUN",
					"request": {
						"method": "DELETE",
						"header": [],
						"body": {
							"mode": "raw",
							"raw": ""
						},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/84/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/0074F",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"84",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"0074F"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation LUN non-existent",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/{{lunid}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"{{lunid}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validation LUN free",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/{{lunid}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"{{lunid}}"
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "a.4 New Masking View",
			"description": "",
			"item": [
				{
					"name": "Validation IP/Endpoint",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/system/version",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"system",
								"version"
							]
						}
					},
					"response": []
				}
			]
		},
		{
			"name": "Miscelaneous",
			"description": "Other API calls",
			"item": [
				{
					"name": "Validation VMAX3 connectivity",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/84/sloprovisioning/symmetrix/{{vmax3_sn}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"84",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate LUN Copy",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/volume/{{lunid}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"volume",
								"{{lunid}}"
							]
						}
					},
					"response": []
				},
				{
					"name": "Validate Storage Group Copy",
					"request": {
						"method": "GET",
						"header": [],
						"body": {},
						"url": {
							"raw": "https://{{u4vmax_ip}}:8443/univmax/restapi/sloprovisioning/symmetrix/{{vmax3_sn}}/storagegroup/{{storagegroup}}",
							"protocol": "https",
							"host": [
								"{{u4vmax_ip}}"
							],
							"port": "8443",
							"path": [
								"univmax",
								"restapi",
								"sloprovisioning",
								"symmetrix",
								"{{vmax3_sn}}",
								"storagegroup",
								"{{storagegroup}}"
							]
						}
					},
					"response": []
				}
			]
		}
	],
	"auth": {
		"type": "basic",
		"basic": [
			{
				"key": "password",
				"value": "C0nnectrix",
				"type": "string"
			},
			{
				"key": "username",
				"value": "vndrtsap",
				"type": "string"
			}
		]
	},
	"event": [
		{
			"listen": "prerequest",
			"script": {
				"id": "2ce6982d-721d-43bf-ab28-b2dcd1fefe68",
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		},
		{
			"listen": "test",
			"script": {
				"id": "d09e5020-612f-40d4-a9e4-897c4dd3c433",
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		}
	],
	"variable": [
		{
			"id": "315dcfa6-bd15-40bc-b45f-f5628fcdd266",
			"key": "u4vmax_ip",
			"value": "10.136.104.96",
			"type": "string",
			"description": ""
		},
		{
			"id": "2c7862c3-f3c5-4b8f-b3c4-c019b751df16",
			"key": "vmax3_sn",
			"value": "000197000564",
			"type": "string",
			"description": ""
		},
		{
			"id": "81828e14-2c49-45d7-a00e-e3f863a3d111",
			"key": "srp_vmax3",
			"value": "SRP_1",
			"type": "string",
			"description": ""
		},
		{
			"id": "37044c4f-be7c-4f8c-abcd-6a91f36a600e",
			"key": "maskingview",
			"value": "ESX_Windows_Dev_mv",
			"type": "string",
			"description": ""
		},
		{
			"id": "8449d571-2cce-4692-bb4b-4cfb6c8c64c4",
			"key": "storagegroup",
			"value": "ESX_Windows_Dev_sg",
			"type": "string",
			"description": ""
		},
		{
			"id": "580db289-268b-466a-888b-b6c167ab68c7",
			"key": "lunid",
			"value": "00FB0",
			"type": "string",
			"description": ""
		}
	]
}

.

