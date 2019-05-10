---
title: FunctionTailcall2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e10b1a77586a09f8f5f7a59e811953fbede8773
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586896"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 — Funkcja
Powiadamia program profilujący, że aktualnie wykonywanej funkcji ma wykonywać wywołania tail do innej funkcji oraz informacje o ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator aktualnie wykonywanej funkcji jest przeprowadzasz ogon wywołania.  
  
 `clientData`  
 [in] Identyfikator funkcji ponownie zmapowany, który program profilujący wcześniej określona za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), aktualnie wykonywanej funkcji, która dokona ogon wywołania.  
  
 `func`  
 [in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.  
  
 Program profilujący powinien traktować to jako nieprzezroczysty uchwyt, który może być przekazywany do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja docelowy wywołania tail użyje bieżącej ramki stosu i zwróci bezpośrednio do obiektu wywołującego zgłaszający tail wywołania funkcji. Oznacza to, że [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) wywołanie zwrotne nie zostanie wystawiony dla funkcji, która jest elementem docelowym wywołania tail.  
  
 Wartość `func` parametr jest nieprawidłowy po `FunctionTailcall2` funkcja zwraca, ponieważ wartość mogą ulec zmianie lub zostać zniszczone.  
  
 `FunctionTailcall2` Funkcji jest wywołanie zwrotne; należy go zaimplementować. Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).  
  
- Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.  
  
 Implementacja `FunctionTailcall2` nie powinny blokować, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych. Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów. Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionTailcall2` zwraca.  
  
 Ponadto `FunctionTailcall2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
