---
title: FunctionTailcall — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11cf96f5957d41e0647c309a7b0bb08fc9b31c91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452107"
---
# <a name="functiontailcall-function"></a>FunctionTailcall — Funkcja
Powiadamia profilera aktualnie wykonywane funkcja o zbliżającym się wykonywać wywołania tail na inną funkcję.  
  
> [!NOTE]
>  `FunctionTailcall` Funkcja jest przestarzała w programie .NET Framework w wersji 2.0. Nadal będzie działać, ale będzie pociągnąć za sobą zmniejszenie wydajności. Użyj [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zamiast tego działania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcID`  
 [in] Identyfikator aktualnie wykonywane funkcji, która wprowadzi tail wywołania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja docelowy wywołania tail użyje bieżącej ramki stosu i zwróci bezpośrednio do obiektu wywołującego zgłaszającego tail wywołania funkcji. Oznacza to, że [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołania zwrotnego nie zostanie wystawiony dla funkcji, która jest elementem docelowym wywołania tail.  
  
 `FunctionTailcall` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować. Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.  
  
 Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.  
  
-   Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).  
  
-   Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.  
  
 Implementacja `FunctionTailcall` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych. Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci. Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionTailcall` zwraca.  
  
 Ponadto `FunctionTailcall` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz też  
 [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
