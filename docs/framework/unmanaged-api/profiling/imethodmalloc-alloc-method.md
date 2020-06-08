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
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494205"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc — Metoda

Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.

## <a name="syntax"></a>Składnia

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametry

`cb`\
podczas Liczba bajtów do przydzielenia dla treści metody.

## <a name="remarks"></a>Uwagi

 Przydzieloną pamięć rozpocznie się pod adresem większym niż adres podstawowy modułu, który jest skojarzony z tym alokatorem. Innymi słowy, każdy Alokator jest tworzony dla danego modułu i podejmie próbę przydzielenia pamięci z przesunięciem pozytywnym od jego adresu podstawowego. Jeśli `Alloc` żądana liczba bajtów w adresie większym niż adres bazowy modułu nie powiedzie się, zwraca E_OUTOFMEMORY, niezależnie od rzeczywistej ilości dostępnego miejsca w pamięci.

 `Alloc`Metoda powinna być używana w połączeniu z metodą [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>Wymagania
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** CorProf. idl, CorProf. h

 **Biblioteka:** CorGuids. lib

 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IMethodMalloc, interfejs](imethodmalloc-interface.md)
