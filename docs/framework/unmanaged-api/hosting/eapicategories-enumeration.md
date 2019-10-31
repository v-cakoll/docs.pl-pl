---
title: EApiCategories — Wyliczenie
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131212"
---
# <a name="eapicategories-enumeration"></a>EApiCategories — Wyliczenie
Opisuje kategorie możliwości, które host może blokować z uruchamiania w częściowo zaufanym kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eAll`|Określa, że wszystkie zarządzane klasy i elementy członkowskie, które są objęte innymi polami `EApiCategories`, nie mogą być uruchamiane w częściowo zaufanym kodzie.|  
|`eExternalProcessMgmt`|Określa, że zarządzane klasy i elementy członkowskie, które umożliwiają tworzenie, manipulowanie i niszczenie procesów zewnętrznych, nie są uruchamiane w częściowo zaufanym kodzie.|  
|`eExternalThreading`|Określa, że zarządzane klasy i elementy członkowskie, które umożliwiają tworzenie, manipulowanie i niszczenie wątków zewnętrznych, nie są uruchamiane w częściowo zaufanym kodzie.|  
|`eMayLeakOnAbort`|Określa, że zarządzane typy i elementy członkowskie, które mogą potencjalnie przeciekać pamięć przy przerwaniu, mogą być uruchamiane w częściowo zaufanym kodzie.|  
|`eNoCategory`|Określa, że nie można blokować uruchamiania żadnej zarządzanej kategorii kodu w kodzie częściowo zaufanym.|  
|`eSecurityInfrastructure`|Określa, że infrastruktura zabezpieczeń środowiska uruchomieniowego języka wspólnego (CLR) nie może być używana przez częściowo zaufany kod.|  
|`eSelfAffectingProcessMgmt`|Określa, że zarządzane klasy i elementy członkowskie, których możliwości mogą mieć wpływ na proces hostowany, można zablokować z uruchamiania w częściowo zaufanym kodzie.|  
|`eSelfAffectingThreading`|Określa, że zarządzane klasy i elementy członkowskie, których możliwości mogą wpływać na wątki w hostowanym procesie, można zablokować uruchamiania w częściowo zaufanym kodzie.|  
|`eSharedState`|Określa, że zarządzane klasy i elementy członkowskie, które uwidaczniają stan udostępniony, nie są uruchamiane w częściowo zaufanym kodzie.|  
|`eSynchronization`|Określa, że klasy środowiska uruchomieniowego języka wspólnego i składowe, które zezwalają na przechowywanie blokad przez kod użytkownika, nie mogą być uruchamiane w częściowo zaufanym kodzie.|  
|`eUI`|Określa, że zarządzane klasy i elementy członkowskie, które zezwalają na interakcję ludzką lub wymagają, aby nie były uruchamiane w częściowo zaufanym kodzie.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda [ICLRHostProtectionManager:: SetProtectedCategories —](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) przyjmuje parametr typu `EApiCategories`.  
  
 Wyliczenie `EApiCategories` i Metoda `SetProtectedCategories` są bezpośrednio powiązane z klasą zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>. Zarządzana Klasa jest używana z wyliczeniem <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, którego wartości odpowiadają bezpośrednio na wartości `EApiCategories`, aby oznaczyć typy zarządzane i składowe, które uwidaczniają możliwości odpowiadające kategoriom opisanym przez `EApiCategories`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
