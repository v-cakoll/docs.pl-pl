---
title: ICLRPolicyManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703475"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager — Interfejs
Dostarcza metody, które pozwalają hostowi określić akcje zasad, które mają być podejmowane w przypadku awarii i przekroczeń limitu czasu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetActionOnFailure, metoda](iclrpolicymanager-setactiononfailure-method.md)|Określa akcję zasad, która ma być wykonywana przez środowisko uruchomieniowe języka wspólnego (CLR) w przypadku wystąpienia określonego błędu.|  
|[SetActionOnTimeout, metoda](iclrpolicymanager-setactionontimeout-method.md)|Określa akcję zasad wykonywaną przez środowisko CLR po przełączeniu określonej operacji.|  
|[SetDefaultAction, metoda](iclrpolicymanager-setdefaultaction-method.md)|Określa akcję zasad wykonywaną przez środowisko CLR po wystąpieniu określonej operacji.|  
|[SetTimeout, metoda](iclrpolicymanager-settimeout-method.md)|Ustawia wartość limitu czasu dla określonej operacji.|  
|[SetTimeoutAndAction, metoda](iclrpolicymanager-settimeoutandaction-method.md)|Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasad, którą powinien wykonać środowisko CLR po wystąpieniu operacji.|  
|[SetUnhandledExceptionPolicy, metoda](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Określa zachowanie środowiska CLR w przypadku wystąpienia nieobsługiwanego wyjątku.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure — Wyliczenie](eclrfailure-enumeration.md)
- [EClrOperation — Wyliczenie](eclroperation-enumeration.md)
- [EPolicyAction — Wyliczenie](epolicyaction-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
