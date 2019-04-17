# KiemTraGiuaKy_071700135
import requests
import json
from tabulate import *
from my_apic_em_functions2 import *
requests.packages.urllib3.disable_warnings()

check_url = api_url + "/" + flowAnalysisId
status = ""
checks = 1
while status != "COMPLETED":
    r = requests.get(check_url, headers=headers, verify=False)
    response_json = r.json()    
    status = response_json["response"]["request"]["status"]   
    print("REQUEST STATUS: ", status)  
    time.sleep(1)
    if checks == 15:  
        raise Exception("Number of status checks exceeds limit. Possible problem with Path Trace.!")
    elif status == "FAILED":       
        raise Exception("Problem with Path Trace - FAILED!")
    checks += 1
