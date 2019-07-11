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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f94867db6908f0999604511d9782b6f5abfb5e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752047"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS — Wyliczenie
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
|COR_PRF_MODULE_NGEN|Moduł został wygenerowany przez Generator obrazu natywnego (Ngen.exe).|  
|COR_PRF_MODULE_DYNAMIC|Moduł został utworzony za pomocą metod <xref:System.Reflection.Emit?displayProperty=nameWithType> przestrzeni nazw.|  
|COR_PRF_MODULE_COLLECTIBLE|Okres istnienia modułu jest zarządzany przez moduł odśmiecania pamięci.|  
|COR_PRF_MODULE_RESOURCE|W module metadanych nie zawiera, są używane wyłącznie jako zasób. Zarządzane wielokrotność ten bit jest <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> metody.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Układ modułu w pamięci jest jednoznaczna, nie jest zamapowany. Jeśli moduł zawiera ten ustawiony bit, profilerów, które odczytują informacje bezpośrednio z przenośnych nagłówka pliku wykonywalnego (PE) będzie mieć należy zachować ostrożność podczas interpretowania względnych adresów wirtualnych (RVA) w nagłówku.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Flaga typu zawartości środowiska uruchomieniowego Windows jest ustawiona w metadanych dla zestawu tego modułu. Dotyczy to wszystkich modułów Windows metadanych (.winmd).|  
  
## <a name="remarks"></a>Uwagi  
 Usługa BITS z cor_prf_module_flags — są zwracane do programu profilującego w `pdwModuleFlags` dane wyjściowe parametru [icorprofilerinfo3::getmoduleinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metody. Niektóre kombinacje co najmniej dwóch flagi są możliwe, ale nie wszystkie kombinacje są możliwe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
