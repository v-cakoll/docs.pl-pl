---
title: CorDebugMappingResult — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2042d0936359a85d203375c42be0d8a096f004e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739762"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult — Wyliczenie
Zawiera szczegółowe informacje, jak uzyskać była wartość wskaźnika instrukcji (IP).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Kod macierzysty znajduje się w prologu, więc wartość adresu IP wynosi 0.|  
|`MAPPING_EPILOG`|Natywny kod znajduje się w epilogu, więc wartość adresu IP jest adresem ostatniej instrukcji metody.|  
|`MAPPING_NO_INFO`|Nie informacji o mapowaniu jest dostępna w przypadku metody, więc wartość adresu IP wynosi 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Mimo że istnieje informacje dotyczące mapowania dla metody, bieżący adres nie można zamapować na kod intermediate language (MSIL) firmy Microsoft. Wartość adresu IP wynosi 0.|  
|`MAPPING_EXACT`|Metoda mapuje dokładnie kod MSIL albo ramki jest interpretowany, więc wartość adresu IP jest dokładne.|  
|`MAPPING_APPROXIMATE`|Metoda został pomyślnie zamapowany, ale wartość adresu IP może być przybliżone.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodę, aby uzyskać wartość wskaźnika instrukcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
