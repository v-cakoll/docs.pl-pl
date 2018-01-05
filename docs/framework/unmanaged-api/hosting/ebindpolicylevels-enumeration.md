---
title: "EBindPolicyLevels — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EBindPolicyLevels
api_location: mscoree.dll
api_type: COM
f1_keywords: EBindPolicyLevels
helpviewer_keywords: EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52e4d4522c7401aba198deed7853ccca71752d83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels — Wyliczenie
Zawiera flagi, aby określić poziom, na których chcesz zastosować lub zmodyfikować zasady zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|Określa, że zasady powinny zostać zastosowane na poziomie administratora.|  
|`ePolicyLevelApp`|Określa, że zasady powinny zostać zastosowane na poziomie aplikacji.|  
|`ePolicyLevelHost`|Określa, że zasady powinny zostać zastosowane na poziomie hosta.|  
|`ePolicyLevelNone`|Określa żadnych flag poziomu zasad.|  
|`ePolicyLevelPublisher`|Określa, że zasady powinny zostać zastosowane na poziomie wydawcy.|  
|`ePolicyLevelRetargetable`|Określa, że zasady powinny mieć zastosowanie na poziomach zmiennej.|  
|`ePolicyPortability`|Określa, że zasady powinny obsługiwać przenoszenia między implementacje zestawu .NET Framework. Zobacz [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) element pliku konfiguracji.|  
|`ePolicyUnifiedToCLR`|Określa, że zasady powinny unified niż środowisko uruchomieniowe języka wspólnego (CLR).|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest przekazywany do metody [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interfejs, aby określić zmiany w zasadach aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
