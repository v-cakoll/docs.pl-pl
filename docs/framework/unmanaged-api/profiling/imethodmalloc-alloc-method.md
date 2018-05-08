---
title: IMethodMalloc::Alloc — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d73fe16720248d541bac64a432bb6f35d6873b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMethodMalloc, interfejs](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
