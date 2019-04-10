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
ms.openlocfilehash: 656f2498c7dd9ba165ab6759d8ca3b26e0d7c93f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207048"
---
# <a name="functiontailcall-function"></a>FunctionTailcall — Funkcja
Powiadamia program profilujący, że aktualnie wykonywanej funkcji zostanie wykonywać wywołania tail do innej funkcji.  
  
> [!NOTE]
>  `FunctionTailcall` Funkcja jest przestarzała w programie .NET Framework 2.0. Nadal będzie działać, ale spowoduje naliczenie opłaty za spadek wydajności. Użyj [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zamiast tego funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcID`  
 [in] Identyfikator aktualnie wykonywanej funkcji jest przeprowadzasz ogon wywołania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja docelowy wywołania tail użyje bieżącej ramki stosu i zwróci bezpośrednio do obiektu wywołującego zgłaszający tail wywołania funkcji. Oznacza to, że [functionleave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) wywołanie zwrotne nie zostanie wystawiony dla funkcji, która jest elementem docelowym wywołania tail.  
  
 `FunctionTailcall` Funkcji jest wywołanie zwrotne; należy go zaimplementować. Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
-   Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).  
  
-   Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.  
  
 Implementacja `FunctionTailcall` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych. Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów. Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionTailcall` zwraca.  
  
 Ponadto `FunctionTailcall` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter2 — Funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 — Funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
