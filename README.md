# KiemTraGiuaKy_071700135
import requests
import json
from my_apic_em_functions2 import *
from tabulate import *
requests.packages.urllib3.disable_warnings()

api_url = "https://SandBoxAPICEM.cisco.com/api/v1/flow-analysis"
ticket = get_ticket()

# Create headers
headers = {
    "content-type": "application/json",
    "X-Auth-Token": ticket
        }

