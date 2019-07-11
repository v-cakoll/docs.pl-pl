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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d70f7dd872cefbadce56c577ce2ecc9cbcb663b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765845"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags — Wyliczenie
Zezwalaj hostowi na określenie typu przekierowania, których środowisko uruchomieniowe języka wspólnego (CLR), należy wykonać podczas stosowania zmian zasad z zestawu źródłowego zestawu docelowego.  
  
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
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Określa, że środowiska CLR będzie łańcucha wartości zasad zestawu źródła na tych dla zestawu docelowego.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Określa, że środowisko CLR wykona domyślne działanie.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Określa, czy środowiska CLR będzie równa wartości zasad dla zestawu docelowego maksymalne wartości.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Określa środowisko CLR spowoduje zastąpienie wartości zasad dla zestawu docelowego z tymi źródło zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrhostbindingpolicymanager::modifyapplicationpolicy —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) metoda przyjmuje parametr typu `EHostBindingPolicyModifyFlags`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
