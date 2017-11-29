---
title: "FunctionLeave — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave
helpviewer_keywords: FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3368a97adf6ffceaa5ac56b7ffe16d6e2802437c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave-function"></a>FunctionLeave — Funkcja
Powiadamia profilera funkcji o zbliżającym się zwrócić do obiektu wywołującego.  
  
> [!NOTE]
>  `FunctionLeave` Funkcja jest przestarzała w .NET Framework 2.0. Nadal będzie działać, ale będzie pociągnąć za sobą zmniejszenie wydajności. Użyj [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zamiast tego działania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcID`  
 [in] Identyfikator funkcji, która zwraca.  
  
## <a name="remarks"></a>Uwagi  
 `FunctionLeave` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować. Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.  
  
 Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.  
  
-   Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).  
  
-   Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.  
  
 Implementacja `FunctionLeave` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych. Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci. Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave` zwraca.  
  
 Ponadto `FunctionLeave` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz też  
 [Functionenter2 — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [Functionleave2 — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Functiontailcall2 — funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Statyczne funkcje globalne profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
