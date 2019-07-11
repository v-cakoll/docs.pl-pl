---
title: GetCachePath — Funkcja
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92366190c769344b41923cbb25ed4b04afceaae9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778671"
---
# <a name="getcachepath-function"></a>GetCachePath — Funkcja
Pobiera ścieżkę do zestawu pamięci podręcznej, przy użyciu określonych flag.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `dwCacheFlags`  
 [in] [Asm_cache_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) wartość, która wskazuje źródło pamięci podręcznej zestawów.  
  
 `pwzCachePath`  
 [out] Zwrócony wskaźnik do ścieżki.  
  
 `pcchPath`  
 [out w] Żądana długość maksymalna `pwzCachePath`, a po powrocie, rzeczywista długość `pwzCachePath`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ASM_CACHE_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
