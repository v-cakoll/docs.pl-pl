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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906376"
---
# <a name="eapicategories-enumeration"></a>EApiCategories — Wyliczenie
Opis kategorii możliwości, które blokują hosta z systemem w kodzie częściowo zaufanym.  
  
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
|`eAll`|Określa, czy wszystkich zarządzanych klas i składowych, które są obejmowane przez inne `EApiCategories` pola zablokowany w kodzie częściowo zaufanym.|  
|`eExternalProcessMgmt`|Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, manipulowanie i niszczenia procesy zewnętrzne zablokowany w kodzie częściowo zaufanym.|  
|`eExternalThreading`|Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, manipulowanie i niszczenie wątków zewnętrznych zablokowany w kodzie częściowo zaufanym.|  
|`eMayLeakOnAbort`|Określa, że zarządzane typy i elementy członkowskie, które potencjalnie mogą spowodować wyciek pamięci po przerwaniu zablokowany w kodzie częściowo zaufanym.|  
|`eNoCategory`|Określa, że nie ma kategorii kodu zarządzanego zablokowany w kodzie częściowo zaufanym.|  
|`eSecurityInfrastructure`|Określa, że zablokowany wspólnej infrastruktury języka wspólnego (CLR) zabezpieczeń używany przez częściowo zaufany kod.|  
|`eSelfAffectingProcessMgmt`|Określa, że zarządzanych klas i składowych, których możliwości mogą mieć wpływ na proces hostowanej zablokowany w kodzie częściowo zaufanym.|  
|`eSelfAffectingThreading`|Określa, że zarządzanych klas i składowych, których możliwości mogą mieć wpływ na wątki w procesie hostowanej zablokowany w kodzie częściowo zaufanym.|  
|`eSharedState`|Określa, że zarządzanych klas i składowych, które uwidaczniają udostępnionego stanu zablokowany w kodzie częściowo zaufanym.|  
|`eSynchronization`|Określa, że wspólnej klasy środowiska wykonawczego języka i elementy członkowskie, które umożliwia blokady przy użyciu kodu użytkownika zablokowany w kodzie częściowo zaufanym.|  
|`eUI`|Określa, że zarządzanych klas i składowych, które blokują lub wymaga interakcji z człowiekiem zablokowany w kodzie częściowo zaufanym.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrhostprotectionmanager::setprotectedcategories —](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda przyjmuje parametr typu `EApiCategories`.  
  
 `EApiCategories` Wyliczenie i `SetProtectedCategories` metoda odnoszą się bezpośrednio do zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> klasy. Klasa zarządzana jest używana z <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> wyliczenia, których wartości odpowiadają bezpośrednio do `EApiCategories` wartości, aby oznaczyć zarządzane typy i elementy członkowskie, które udostępniają funkcje odpowiadającej kategorii opisanych przez `EApiCategories`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
