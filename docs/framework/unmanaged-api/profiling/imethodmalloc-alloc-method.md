---
title: "IMethodMalloc::Alloc — Metoda"
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
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc — Metoda
Próbuje przydzielić określonej ilości pamięci dla nowego treści funkcji języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cb`  
 [in] Liczba bajtów do przydzielenia dla treści metody.  
  
## <a name="remarks"></a>Uwagi  
 Pod adresem większy niż adres bazowy moduł, który jest skojarzony z tym alokatora rozpocznie się alokacji pamięci. Innymi słowy każdego programu przydzielania jest tworzony dla danego modułu i podejmie próbę przydzielenia pamięci z przesunięciem dodatnią z jego adres podstawowy. Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większy niż adres bazowy moduł, zwraca E_OUTOFMEMORY, niezależnie od rzeczywistej ilości miejsca w pamięci.  
  
 `Alloc` Metody powinny być używane w połączeniu z [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** WindSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMethodMalloc, interfejs](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
