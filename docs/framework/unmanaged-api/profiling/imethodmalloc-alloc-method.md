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
ms.openlocfilehash: 54c38f9a9abc9a02ba4d84c9a41b2ef6b1f7cb69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528566"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc — Metoda
Próbuje przydzielić określonej ilości pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).  
  
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
 Ilość przydzielonej pamięci rozpocznie się pod adresem większy niż adres podstawowy moduł, który jest skojarzony z tym alokatora. Innymi słowy każdy alokatora jest tworzona dla danego modułu i podejmie próbę przydzielenia pamięci na dodatnią przesunięcie z adresu podstawowego. Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większy niż adres podstawowy moduł, zwraca E_OUTOFMEMORY niezależnie od rzeczywistej ilości miejsca w pamięci.  
  
 `Alloc` Metoda powinna służyć w połączeniu z [icorprofilerinfo::setilfunctionbody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** WindSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMethodMalloc, interfejs](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
