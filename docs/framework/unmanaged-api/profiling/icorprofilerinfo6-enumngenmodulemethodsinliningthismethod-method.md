---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495531"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda

Zwraca moduł wyliczający do wszystkich metod, które są zdefiniowane w danym module NGen i wbudowana daną metodę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>Parametry

`inlinersModuleId`\
podczas Identyfikator modułu NGen.

`inlineeModuleId`\
podczas Identyfikator modułu, który definiuje `inlineeMethodId` . Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

`inlineeMethodId`\
podczas Identyfikator metody wbudowanej. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

`incompleteData`\
określoną Flaga wskazująca, czy `ppEnum` zawiera wszystkie metody podkreślające daną metodę.  Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.

`ppEnum`\
określoną Wskaźnik do adresu modułu wyliczającego

## <a name="remarks"></a>Uwagi

`inlineeModuleId`i `inlineeMethodId` razem tworzą pełny identyfikator dla metody, która może być wbudowana. Na przykład załóżmy, że moduł `A` definiuje metodę `Simple.Add` :

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

i moduł B definiuje `Fancy.AddTwice` :

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Umożliwia również założenie, że `Fancy.AddTwice` wywołanie `SimpleAdd` . Profiler może użyć tego modułu wyliczającego, aby znaleźć wszystkie metody zdefiniowane w module B `Simple.Add` , które są wbudowane, a wynikiem będzie Wyliczenie `AddTwice` .  `inlineeModuleId`jest identyfikatorem modułu `A` i `inlineeMethodId` jest identyfikatorem `Simple.Add(int a, int b)` .

Jeśli `incompleteData` wartość jest równa true po zwracaniu funkcji, moduł wyliczający nie zawiera wszystkich metod, które podkreślają daną metodę. Może to być spowodowane tym, że co najmniej jedna bezpośrednia lub pośrednia zależność modułu modułów nie została jeszcze załadowana. Jeśli Profiler wymaga dokładnej ilości danych, powinien ponowić próbę później, gdy więcej modułów zostanie załadowanych, najlepiej przy każdym załadowaniu modułu.

`EnumNgenModuleMethodsInliningThisMethod`Metoda może służyć do obejścia ograniczeń dotyczących deReJIT. ReJIT umożliwia usłudze Profiler zmianę implementacji metody, a następnie utworzenie nowego kodu na bieżąco. Na przykład możemy zmienić `Simple.Add` w następujący sposób:

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Mimo że `Fancy.AddTwice` funkcja została już wbudowana `Simple.Add` , nadal ma takie samo zachowanie jak wcześniej. Aby obejść to ograniczenie, obiekt wywołujący musi wyszukać wszystkie metody we wszystkich modułach, które są wbudowane `Simple.Add` i używane `ICorProfilerInfo5::RequestRejit` dla każdej z tych metod. Po ponownym skompilowaniu metod będą one miały nowe zachowanie `Simple.Add` zamiast starego zachowania.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**.NET Framework wersje:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo6, interfejs](icorprofilerinfo6-interface.md)
