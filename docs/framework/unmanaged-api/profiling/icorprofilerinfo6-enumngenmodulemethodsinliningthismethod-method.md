---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568156"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
[Obsługiwane w programie .NET Framework 4.6 lub nowszy]  
  
 Zwraca moduł wyliczający do metod, które są zdefiniowane w danym module NGen i wbudowane danej metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `inlinersModuleId`  
 [in] Identyfikator modułu NGen.  
  
 `inlineeModuleId`  
 [in] Identyfikator modułu, który definiuje `inlineeMethodId`. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `inlineeMethodId`  
 [in] Identyfikator śródwierszowych metody. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `incompleteData`  
 [out] Flaga, która wskazuje, czy `ppEnum` zawiera wszystkie metody wbudowanie danej metody.  Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `ppEnum`  
 [out] Wskaźnik na adres modułu wyliczającego  
  
## <a name="remarks"></a>Uwagi  
 `inlineeModuleId` i `inlineeMethodId` razem tworzą pełny identyfikator metodę, która może być śródwierszowa. Załóżmy na przykład moduł `A` definiuje metodę `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 Moduł Bdefines i `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Umożliwia także przyjęto założenie, że `Fancy.AddTwice` inlines wywołanie do `SimpleAdd`. Program profilujący można użyć tego modułu wyliczającego można znaleźć wszystkie metody zdefiniowanego w module B, której wbudowane `Simple.Add`, i wynik będzie wyliczanie `AddTwice`.  `inlineeModuleId` Identyfikator modułu `A`, i `inlineeeMethodId` jest identyfikatorem `Simple.Add(int a, int b)`.  
  
 Jeśli `incompleteData` ma wartość true po funkcji zwraca wartość modułu wyliczającego nie zawiera wszystkich metod wbudowanie danej metody. Może się to zdarzyć, gdy dla jednego lub więcej bezpośrednich lub pośrednich zależności inliners moduł nie został jeszcze załadowany. Jeśli program profilujący musi dokładnych danych, należy ponowić próbę później podczas więcej są załadowane moduły, najlepiej podczas każdego ładowania modułu.  
  
 `EnumNgenModuleMethodsInliningThisMethod` Metoda może służyć do obejścia ograniczeń na wbudowanie dla ReJIT. ReJIT informuje program profilujący Zmień implementację metody, a następnie utwórz nowy kod go na bieżąco. Na przykład można zmienić `Simple.Add` w następujący sposób:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Jednak ponieważ `Fancy.AddTwice` ma już śródwierszowych `Simple.Add`, będzie nadal mają takie samo zachowanie, tak jak poprzednio. W celu obejścia tego ograniczenia, obiekt wywołujący ma wyszukiwać wszystkie metody we wszystkich modułach tym miejscu `Simple.Add` i użyj `ICorProfilerInfo5::RequestRejit` na każdym z tych metod. Gdy metody są ponownie skompilowany, muszą nowe zachowanie `Simple.Add` zamiast stare zachowanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
