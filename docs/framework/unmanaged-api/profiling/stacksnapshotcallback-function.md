---
title: StackSnapshotCallback — Funkcja
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493997"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback — Funkcja
Zapewnia profilerowi informacje o każdej zarządzanej ramce i każdym uruchomieniu niezarządzanych ramek na stosie podczas przechodzenia stosu, który jest inicjowany przez [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 podczas Jeśli ta wartość jest równa zero, to wywołanie zwrotne dotyczy przebiegu ramek niezarządzanych; w przeciwnym razie jest to identyfikator funkcji zarządzanej, a to wywołanie zwrotne dotyczy ramki zarządzanej.  
  
 `ip`  
 podczas Wartość wskaźnika instrukcji kodu natywnego w ramce.  
  
 `frameInfo`  
 podczas `COR_PRF_FRAME_INFO`Wartość, która odwołuje się do informacji o ramce stosu. Ta wartość jest prawidłowa do użycia tylko w trakcie tego wywołania zwrotnego.  
  
 `contextSize`  
 podczas Rozmiar `CONTEXT` struktury, do której odwołuje się `context` parametr.  
  
 `context`  
 podczas Wskaźnik do `CONTEXT` struktury Win32, który reprezentuje stan procesora CPU dla tej ramki.  
  
 `context`Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przeniesiona `ICorProfilerInfo2::DoStackSnapshot` .  
  
 `clientData`  
 podczas Wskaźnik do danych klienta, który jest przenoszona bezpośrednio przez z `ICorProfilerInfo2::DoStackSnapshot` .  
  
## <a name="remarks"></a>Uwagi  
 `StackSnapshotCallback`Funkcja jest implementowana przez moduł zapisujący profilera. Należy ograniczyć złożoność pracy wykonywanej w programie `StackSnapshotCallback` . Na przykład w przypadku użycia `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny wątek docelowy może być zablokowany. Jeśli kod w ramach `StackSnapshotCallback` wymaga tych samych blokad, może nastąpić zakleszczenie.  
  
 `ICorProfilerInfo2::DoStackSnapshot`Metoda wywołuje `StackSnapshotCallback` funkcję jeden raz dla każdej zarządzanej ramki lub raz na uruchomienie niezarządzanych ramek. Jeśli `StackSnapshotCallback` jest wywoływana w przypadku uruchamiania ramek niezarządzanych, profiler może użyć kontekstu rejestru (przywoływanego przez `context` parametr) do wykonania własnego przeszukiwania niezarządzanego stosu. W takim przypadku `CONTEXT` Struktura Win32 reprezentuje stan procesora dla ostatnio wypchniętej ramki w ramach przebiegu ramek niezarządzanych. Chociaż struktura Win32 `CONTEXT` zawiera wartości dla wszystkich rejestrów, należy polegać tylko na wartościach rejestru wskaźnika stosu, rejestracji wskaźnika ramki, rejestracji wskaźnika instrukcji i nietrwałych (przechowywanych) rejestrów liczb całkowitych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DoStackSnapshot, metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
