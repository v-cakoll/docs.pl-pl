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
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796906"
---
# <a name="getcachepath-function"></a>GetCachePath — Funkcja
Pobiera ścieżkę do buforowanego zestawu przy użyciu określonych flag.  
  
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
 podczas Wartość [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) , która wskazuje Źródło buforowanego zestawu.  
  
 `pwzCachePath`  
 określoną Zwrócony wskaźnik do ścieżki.  
  
 `pcchPath`  
 [in. out] Żądana Maksymalna długość `pwzCachePath`i po powrocie — rzeczywista `pwzCachePath`długość.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ASM_CACHE_FLAGS, wyliczenie](asm-cache-flags-enumeration.md)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
