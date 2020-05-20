---
title: ICLRHostBindingPolicyManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703571"
---
# <a name="iclrhostbindingpolicymanager-interface"></a>ICLRHostBindingPolicyManager — Interfejs
Dostarcza metody dla hosta do szacowania bieżących zasad powiązań i przekazywania zmian zasad dla określonego zestawu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluatePolicy, metoda](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|Oblicza zasady powiązań w imieniu hosta.|  
|[ModifyApplicationPolicy, metoda](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|Modyfikuje zasady powiązań dla określonego zestawu i tworzy nową wersję zasad.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyIdentityManager, interfejs](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore, interfejs](ihostassemblystore-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
