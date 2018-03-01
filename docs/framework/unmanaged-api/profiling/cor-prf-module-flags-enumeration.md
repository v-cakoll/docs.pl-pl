---
title: "COR_PRF_MODULE_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 727816a674d2357c8a9ba1f19679c57669e92f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS — Wyliczenie
Określa właściwości modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|COR_PRF_MODULE_COLLECTIBLE|Okres istnienia modułu jest zarządzana przez moduł garbage collector.|  
|COR_PRF_MODULE_RESOURCE|Moduł zawiera Brak metadanych i są używane wyłącznie jako zasób. Jest odpowiednikiem zarządzanych ten bit <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> metody.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Układ modułu w pamięci jest prosty, nie jest zamapowany. Jeśli moduł ten bit ustawił, profilowania, które zapoznały informacje bezpośrednio z przenośnym nagłówka pliku wykonywalnego (PE) należy zachować ostrożność podczas interpretacji względnych adresów wirtualnych (RVAs) w nagłówku.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Dla tego modułu zestawu w metadanych jest ustawiona flaga zawartości typu środowiska wykonawczego systemu Windows. Dotyczy to wszystkich modułów metadanych systemu Windows (.winmd).|  
  
## <a name="remarks"></a>Uwagi  
 Usługi BITS z cor_prf_module_flags — nastąpi powrót do profilera w `pdwModuleFlags` parametru output [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metody. Niektóre kombinacje dwóch lub więcej flag jest możliwe, ale nie wszystkie połączenia są możliwe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
