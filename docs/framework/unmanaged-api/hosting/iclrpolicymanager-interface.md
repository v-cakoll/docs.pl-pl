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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eeccc4dfd7a7147fe791444eeeca2bd3a844305
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211052"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager — Interfejs
Udostępnia metody, które umożliwiają hosta określić zasady działań podejmowanych w przypadku awarii lub przekroczenia limitu czasu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetActionOnFailure, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|Określa akcję zasad, których środowisko uruchomieniowe języka wspólnego (CLR) powinna wykonać, gdy wystąpi awaria określonej.|  
|[SetActionOnTimeout, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|Określa akcję zasady, którą środowisko CLR powinna wykonać, gdy upłynie limit czasu określonej operacji.|  
|[SetDefaultAction, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|Określa akcję zasady, którą środowisko CLR powinna wykonać, gdy występuje określonej operacji.|  
|[SetTimeout, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|Ustawia wartość limitu czasu dla określonej operacji.|  
|[SetTimeoutAndAction, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|Ustawia wartość limitu czasu dla określonej operacji i określa akcję zasady, którą środowisko CLR powinna wykonać, gdy operacja jest wykonywana.|  
|[SetUnhandledExceptionPolicy, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Określa zachowanie środowiska CLR, po wystąpieniu nieobsługiwanego wyjątku.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
