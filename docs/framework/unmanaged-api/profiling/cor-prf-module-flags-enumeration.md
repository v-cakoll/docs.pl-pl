---
title: COR_PRF_MODULE_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
ms.openlocfilehash: 12e7faa8d9fee7698de9d9734f522d818f225c84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500822"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS — Wyliczenie
Określa właściwości modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Moduł został załadowany z dysku.|  
|COR_PRF_MODULE_NGEN|Moduł został wygenerowany przez generator obrazu natywnego (Ngen. exe).|  
|COR_PRF_MODULE_DYNAMIC|Moduł został utworzony za pomocą metod w <xref:System.Reflection.Emit?displayProperty=nameWithType> przestrzeni nazw.|  
|COR_PRF_MODULE_COLLECTIBLE|Okres istnienia modułu jest zarządzany przez moduł wyrzucania elementów bezużytecznych.|  
|COR_PRF_MODULE_RESOURCE|Moduł nie zawiera żadnych metadanych i jest używany wyłącznie jako zasób. Zarządzanym odpowiednikiem tego bitu jest <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> Metoda.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Układ modułu w pamięci jest płaski, nie zamapowany. Jeśli moduł ma ten bit zestawu, program do odczytywania informacji bezpośrednio z nagłówka pliku przenośnego wykonywalnego (PE) będzie musiał zachować ostrożność podczas interpretacji względnych adresów wirtualnych (RVA) w nagłówku.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Flaga typu zawartości środowisko wykonawcze systemu Windows jest ustawiana w metadanych dla zestawu tego modułu. Dotyczy to wszystkich modułów metadanych systemu Windows (WinMD).|  
  
## <a name="remarks"></a>Uwagi  
 Bity z COR_PRF_MODULE_FLAGS są zwracane do profilera w `pdwModuleFlags` parametrze Output metody [ICorProfilerInfo3:: GetModuleInfo2 —](icorprofilerinfo3-getmoduleinfo2-method.md) . Niektóre kombinacje co najmniej dwóch flag są możliwe, ale nie wszystkie kombinacje są możliwe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
