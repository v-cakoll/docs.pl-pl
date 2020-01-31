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
ms.openlocfilehash: 0f6fb469aa9d6d40b762bfd2feec28c28299732f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867116"
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Moduł został załadowany z dysku.|  
|COR_PRF_MODULE_NGEN|Moduł został wygenerowany przez generator obrazu natywnego (Ngen. exe).|  
|COR_PRF_MODULE_DYNAMIC|Moduł został utworzony przy użyciu metod w przestrzeni nazw <xref:System.Reflection.Emit?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_COLLECTIBLE|Okres istnienia modułu jest zarządzany przez moduł wyrzucania elementów bezużytecznych.|  
|COR_PRF_MODULE_RESOURCE|Moduł nie zawiera żadnych metadanych i jest używany wyłącznie jako zasób. Zarządzany odpowiednik tego bitu jest metodą <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Układ modułu w pamięci jest płaski, nie zamapowany. Jeśli moduł ma ten bit zestawu, program do odczytywania informacji bezpośrednio z nagłówka pliku przenośnego wykonywalnego (PE) będzie musiał zachować ostrożność podczas interpretacji względnych adresów wirtualnych (RVA) w nagłówku.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Flaga typu zawartości środowisko wykonawcze systemu Windows jest ustawiana w metadanych dla zestawu tego modułu. Dotyczy to wszystkich modułów metadanych systemu Windows (WinMD).|  
  
## <a name="remarks"></a>Uwagi  
 Bity z COR_PRF_MODULE_FLAGS są zwracane do profilera w parametrze wyjściowym `pdwModuleFlags` metody [ICorProfilerInfo3:: GetModuleInfo2 —](icorprofilerinfo3-getmoduleinfo2-method.md) . Niektóre kombinacje co najmniej dwóch flag są możliwe, ale nie wszystkie kombinacje są możliwe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
