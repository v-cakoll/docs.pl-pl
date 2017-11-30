---
title: "EApiCategories — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a>EApiCategories — Wyliczenie
Opis kategorii możliwości, które host może zablokować uruchamianie w częściowo zaufany kod.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`eAll`|Określa wszystkie zarządzane klasy i elementów członkowskich, które są objęte przez inne `EApiCategories` pola zablokowane w programie częściowo zaufany kod.|  
|`eExternalProcessMgmt`|Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, modyfikowanie i zniszczenie procesów zewnętrznych zablokowany w programie częściowo zaufany kod.|  
|`eExternalThreading`|Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, manipulowanie i niszczenie wątków zewnętrznych zablokowany w programie częściowo zaufany kod.|  
|`eMayLeakOnAbort`|Określa, że typy zarządzane i elementów członkowskich, które potencjalnie może wyciek pamięci na przerwania zablokowany w programie częściowo zaufany kod.|  
|`eNoCategory`|Określa, że zablokowany żadnych kategorii kodu zarządzanego w programie częściowo zaufany kod.|  
|`eSecurityInfrastructure`|Określa, że zablokowany wspólną infrastrukturę zabezpieczeń dla języka wspólnego (CLR) używanych przez kod częściowo zaufany.|  
|`eSelfAffectingProcessMgmt`|Określa, że zarządzanych klas i członków, których możliwości mogą mieć wpływ na proces hostowanej zablokowany w programie częściowo zaufany kod.|  
|`eSelfAffectingThreading`|Określa, że zarządzanych klas i członków, których możliwości mogą mieć wpływ na wątki w procesie hostowanej zablokowany w programie częściowo zaufany kod.|  
|`eSharedState`|Określa, że zarządzanych klas i elementów członkowskich, które udostępniają stan współużytkowany zablokowany w programie częściowo zaufany kod.|  
|`eSynchronization`|Określa, że typowe klasy środowiska uruchomieniowego języka i elementy członkowskie, które kodu użytkownika pomieścić blokad zablokowany w programie częściowo zaufany kod.|  
|`eUI`|Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają lub wymaga interakcji zablokowany w programie częściowo zaufany kod.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda przyjmuje parametr typu `EApiCategories`.  
  
 `EApiCategories` Wyliczenie i `SetProtectedCategories` metody odnoszą się bezpośrednio do zarządzanego <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> klasy. Zarządzanej klasy jest używany z <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> wyliczenia, których wartości odpowiada bezpośrednio do `EApiCategories` wartości, aby oznaczyć typy zarządzane i elementów członkowskich, które ujawnia możliwości odpowiadający kategorii opisanego przez `EApiCategories`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRHostProtectionManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
