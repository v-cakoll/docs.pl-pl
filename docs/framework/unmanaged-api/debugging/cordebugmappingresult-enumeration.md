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
ms.openlocfilehash: fc3f77adf33502bfbc3d65ff5131420093fbbec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097939"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult — Wyliczenie
Zawiera szczegółowe informacje o sposobie uzyskiwania wartości wskaźnika instrukcji (IP).  
  
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
|`MAPPING_PROLOG`|Kod natywny znajduje się w prologu, więc wartość adresu IP wynosi 0.|  
|`MAPPING_EPILOG`|Kod natywny znajduje się w epilogu, więc wartość adresu IP jest adresem ostatniej instrukcji metody.|  
|`MAPPING_NO_INFO`|Dla metody nie są dostępne żadne informacje o mapowaniu, dlatego wartość adresu IP wynosi 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Chociaż istnieją informacje dotyczące mapowania dla metody, nie można zamapować bieżącego adresu na kod języka pośredniego firmy Microsoft (MSIL). Wartość adresu IP wynosi 0.|  
|`MAPPING_EXACT`|Metoda jest mapowana dokładnie na kod MSIL lub ramka została zinterpretowana, więc wartość adresu IP jest dokładna.|  
|`MAPPING_APPROXIMATE`|Metoda została pomyślnie zmapowana, ale wartość adresu IP może być przybliżona.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wartość wskaźnika instrukcji, można użyć metody [ICorDebugILFrame:: GetIP —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
