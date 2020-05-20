---
title: ICLRHostProtectionManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: 7b1fc70380fff3c551c56043f49c2deda507e366
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703838"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager — Interfejs
Umożliwia hostowi blokowanie określonych zarządzanych klas, metod, właściwości i pól z uruchamiania w częściowo zaufanym kodzie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Zapewnia gwarancję, że niektóre rzadkie sytuacje wyścigu, które mogą spowodować krytyczne błędy środowiska uruchomieniowego języka wspólnego (CLR), nigdy nie będą występowały.|  
|[SetProtectedCategories, metoda](iclrhostprotectionmanager-setprotectedcategories-method.md)|Określa kategorie typów zarządzanych i członków, których uruchamianie ma być blokowane w kodzie częściowo zaufanym.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EApiCategories, wyliczenie](eapicategories-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
