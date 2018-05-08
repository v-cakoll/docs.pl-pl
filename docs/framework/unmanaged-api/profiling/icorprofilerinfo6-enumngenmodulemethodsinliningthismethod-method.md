---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod — metoda
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 564f3b1cdfab2a3020b6bb5ac8d9af03c6532c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod — metoda
[Obsługiwane w programie .NET Framework 4.6 i nowszymi wersjami]  
  
 Zwraca moduł wyliczający wszystkie metody, które są zdefiniowane w podanym module NGen i wbudowanego danej metody.  
  
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
 [in] Identyfikator metody śródwierszowych. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `incompleteData`  
 [out] Flaga, która wskazuje, czy `ppEnum` zawiera wszystkie metody ze śródwierszowaniem danej metody.  Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `ppEnum`  
 [out] Wskaźnik do adresów modułu wyliczającego  
  
## <a name="remarks"></a>Uwagi  
 `inlineeModuleId` i `inlineeMethodId` tworzą pełny identyfikator metody, które mogą być wbudowane. Załóżmy na przykład, moduł `A` definiuje metodę `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 Moduł Bdefines i `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Umożliwia również założyć, że `Fancy.AddTwice` inlines wywołania do `SimpleAdd`. Profiler można użyć tego modułu wyliczającego można znaleźć wszystkie metody zdefiniowanego w module B, który wbudowanego `Simple.Add`, i czy wyliczania wynik `AddTwice`.  `inlineeModuleId` jest to identyfikator modułu `A`, i `inlineeeMethodId` jest identyfikatorem `Simple.Add(int a, int b)`.  
  
 Jeśli `incompleteData` ma wartość true po funkcja zwraca moduł wyliczający nie zawiera wszystkich metod ze śródwierszowaniem danej metody. Może się to zdarzyć, gdy dla jednego lub więcej bezpośrednie lub pośrednie zależności inliners modułu nie zostały jeszcze załadowane. Jeśli profilera musi dokładnych danych, jej powinna ponownie później ładowane więcej modułów, najlepiej na każdym załadowanie modułu.  
  
 `EnumNgenModuleMethodsInliningThisMethod` Metody można użyć w celu obejścia ograniczenia na ze śródwierszowaniem dla ReJIT. ReJIT umożliwia profilera, zmień implementację metody, a następnie utwórz nowy kod dla niego na bieżąco. Na przykład można zmienić `Simple.Add` w następujący sposób:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Jednak ponieważ `Fancy.AddTwice` ma już wbudowanego `Simple.Add`, nadal mają takie samo zachowanie jak poprzednio. W celu obejścia tego ograniczenia, wywołujący ma wyszukiwania dla wszystkich metod we wszystkich modułach tym miejscu `Simple.Add` i użyj `ICorProfilerInfo5::RequestRejit` na każdym z tych metod. Gdy metody są skompilowane ponownie, mają też nowe zachowanie `Simple.Add` zamiast poprzednie działanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
