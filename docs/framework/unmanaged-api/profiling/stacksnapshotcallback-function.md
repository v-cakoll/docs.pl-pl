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
ms.openlocfilehash: 49e154ade91ea1a207645f924bd8aea1dbdb635c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868125"
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
 podczas Wartość `COR_PRF_FRAME_INFO`, która odwołuje się do informacji o ramce stosu. Ta wartość jest prawidłowa do użycia tylko w trakcie tego wywołania zwrotnego.  
  
 `contextSize`  
 podczas Rozmiar struktury `CONTEXT`, do której odwołuje się parametr `context`.  
  
 `context`  
 podczas Wskaźnik do struktury `CONTEXT` Win32, który reprezentuje stan procesora CPU dla tej ramki.  
  
 Parametr `context` jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przeniesiona w `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 podczas Wskaźnik do danych klienta, który jest przenoszona bezpośrednio przez z `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja `StackSnapshotCallback` jest implementowana przez moduł zapisujący profilera. Należy ograniczyć złożoność pracy wykonywanej w `StackSnapshotCallback`. Na przykład w przypadku używania `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny wątek docelowy może być zablokowany. Jeśli kod w `StackSnapshotCallback` wymaga tych samych blokad, może nastąpić zakleszczenie.  
  
 Metoda `ICorProfilerInfo2::DoStackSnapshot` wywołuje funkcję `StackSnapshotCallback` raz dla każdej zarządzanej ramki lub raz na uruchomienie niezarządzanych ramek. Jeśli `StackSnapshotCallback` jest wywoływana w przypadku uruchamiania ramek niezarządzanych, profiler może użyć kontekstu rejestru (przywoływanego przez parametr `context`) do wykonania własnego przeszukiwania niezarządzanego stosu. W takim przypadku struktura `CONTEXT` Win32 reprezentuje stan procesora dla ostatnio wypchniętej ramki w ramach przebiegu ramek niezarządzanych. Mimo że struktura `CONTEXT` Win32 zawiera wartości dla wszystkich rejestrów, należy polegać tylko na wartościach rejestru wskaźnika stosu, rejestracji wskaźnika ramki, rejestru wskaźnika instrukcji i nietrwałych (przechowywanych) rejestrów liczb całkowitych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DoStackSnapshot, metoda](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
