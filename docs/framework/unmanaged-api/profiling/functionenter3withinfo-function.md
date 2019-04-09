---
title: FunctionEnter3WithInfo — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e086f54865307e116a9e522b2fbadee8502249
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105680"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo — Funkcja
Powiadamia program profilujący, że formant jest przekazywany do funkcji, a także uchwyt, który może być przekazywany do [icorprofilerinfo3::getfunctionenter3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) można pobrać argumenty ramki i funkcję stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionIDOrClientID`  
 [in] Identyfikator funkcji, do której kontrola jest przekazywana.  
  
 `eltInfo`  
 [in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym. Tego dojścia jest prawidłowy tylko podczas wywołania zwrotnego, do którego jest przekazywany.  
  
## <a name="remarks"></a>Uwagi  
 `FunctionEnter3WithInfo` Metody wywołania zwrotnego powiadamia program profilujący, ponieważ funkcje są nazywane i włącza program profilujący do użycia [icorprofilerinfo3::getfunctionenter3info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) Aby sprawdzić wartości argumentu. Dostęp do informacji argumentu `COR_PRF_ENABLE_FUNCTION_ARGS` flagi musi zostać ustawione. Można użyć programu profilującego [icorprofilerinfo::seteventmask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzenia, a następnie użyj [icorprofilerinfo3::setenterleavefunctionhooks3withinfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) można zarejestrować usługi Implementacja tej funkcji.  
  
 `FunctionEnter3WithInfo` Funkcji jest wywołanie zwrotne; należy go zaimplementować. Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
-   Przy uruchamianiu musisz najpierw zapisać wszystkich rejestrów, z których korzysta Licencjobiorca, łącznie z programami znajdującymi się na jednostki zmiennoprzecinkowej (FPU).  
  
-   Na zakończenie możesz przywrócić stosu, usuwanie, wyłączanie wszystkich parametrów, które zostały wypchnięte przez wywołującego.  
  
 Implementacja `FunctionEnter3WithInfo` powinien blokuje, ponieważ zostanie opóźnione, wyrzucanie elementów bezużytecznych. Implementacja nie powinien podejmować wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznego dla kolekcji wyrzucania elementów. Jeśli próba zostanie podjęta wyrzucania elementów bezużytecznych, środowisko uruchomieniowe spowoduje zablokowanie aż do `FunctionEnter3WithInfo` zwraca.  
  
 `FunctionEnter3WithInfo` Funkcji nie może wywoływać kod zarządzany lub spowodować alokacji pamięci zarządzanej w dowolny sposób.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
