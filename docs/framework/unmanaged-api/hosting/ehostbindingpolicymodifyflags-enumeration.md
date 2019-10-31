---
title: EHostBindingPolicyModifyFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: a2faf22b48dd0b809d6c3668a37f2119733a9b18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129446"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags — Wyliczenie
Umożliwia hostowi określenie typu przekierowania, który powinien być wykonywany przez środowisko uruchomieniowe języka wspólnego (CLR), gdy stosowane są modyfikacje zasad z zestawu źródłowego do zestawu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Określa, że środowisko CLR będzie przeciągać wartości zasad zestawu źródłowego na te, które są określone dla zestawu docelowego.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Określa, że środowisko CLR wykona akcję domyślną.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Określa, że środowisko CLR ustawi wartości z zestawu docelowego na wartości maksymalne.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Określa, że środowisko CLR zamieni wartości zasad zestawu docelowego na te z zestawu źródłowego.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) przyjmuje parametr typu `EHostBindingPolicyModifyFlags`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
