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
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447568"
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

 Przydzieloną pamięć rozpocznie się pod adresem większym niż adres podstawowy modułu, który jest skojarzony z tym alokatorem. Innymi słowy, każdy Alokator jest tworzony dla danego modułu i podejmie próbę przydzielenia pamięci z przesunięciem pozytywnym od jego adresu podstawowego. Jeśli `Alloc` nie może przydzielić żądanej liczby bajtów pod adresem większym niż adres bazowy modułu, zwraca E_OUTOFMEMORY, niezależnie od rzeczywistej ilości dostępnego miejsca w pamięci.

 Metoda `Alloc` powinna być używana w połączeniu z metodą [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>Wymagania
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** CorProf. idl, CorProf. h

 **Biblioteka:** CorGuids. lib

 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IMethodMalloc, interfejs](imethodmalloc-interface.md)
