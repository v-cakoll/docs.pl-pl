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
ms.openlocfilehash: 9a676989bdc6866f85fabe3e15b1e6b7b8b5a9a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000717"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc — Metoda

Próbuje przydzielić określonej ilości pamięci dla nowej treści funkcji Microsoft intermediate language (MSIL).

## <a name="syntax"></a>Składnia

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametry

`cb`\
[in] Liczba bajtów do przydzielenia dla treści metody.

## <a name="remarks"></a>Uwagi

 Ilość przydzielonej pamięci rozpocznie się pod adresem większy niż adres podstawowy moduł, który jest skojarzony z tym alokatora. Innymi słowy każdy alokatora jest tworzona dla danego modułu i podejmie próbę przydzielenia pamięci na dodatnią przesunięcie z adresu podstawowego. Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większy niż adres podstawowy moduł, zwraca E_OUTOFMEMORY niezależnie od rzeczywistej ilości miejsca w pamięci.

 `Alloc` Metoda powinna służyć w połączeniu z [icorprofilerinfo::setilfunctionbody —](icorprofilerinfo-setilfunctionbody-method.md) metody.

## <a name="requirements"></a>Wymagania
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** CorProf.idl, CorProf.h

 **Biblioteka:** CorGuids.lib

 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IMethodMalloc, interfejs](imethodmalloc-interface.md)