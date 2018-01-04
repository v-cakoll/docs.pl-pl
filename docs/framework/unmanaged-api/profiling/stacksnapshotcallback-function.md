---
title: "StackSnapshotCallback — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackSnapshotCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: StackSnapshotCallback
helpviewer_keywords: StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback — Funkcja
Zawiera informacje o każdej ramce zarządzanych i każdym uruchomieniu niezarządzane ramek na stosie podczas przeszukiwania stosu, który jest inicjowane przez profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Jeśli ta wartość wynosi zero, to wywołanie zwrotne jest dla przebiegu niezarządzane ramek; w przeciwnym razie jest identyfikator zarządzanego funkcji i jest to wywołanie zwrotne dla ramki zarządzane.  
  
 `ip`  
 [in] Wartość wskaźnika instrukcji kodu macierzystego w ramce.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` wartość, która odwołuje się do informacji na temat ramki stosu. Ta wartość jest prawidłowa do stosowania tylko podczas tego wywołania zwrotnego.  
  
 `contextSize`  
 [in] Rozmiar `CONTEXT` struktury, która odwołuje się do niego `context` parametru.  
  
 `context`  
 [in] Wskaźnik do Win32 `CONTEXT` strukturę, która reprezentuje stan procesora CPU dla tej ramki.  
  
 `context` Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przekazana `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Wskaźnik do danych klienta, który jest przekazywane bezpośrednio z `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Uwagi  
 `StackSnapshotCallback` Funkcji jest implementowany przez twórcę profilera. Należy ograniczyć złożoność pracować `StackSnapshotCallback`. Na przykład w przypadku korzystania z `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny wątek docelowy może być blokują. Jeśli kod w `StackSnapshotCallback` wymaga tego samego blokad, może nastąpić zakleszczenie.  
  
 `ICorProfilerInfo2::DoStackSnapshot` Wywołania metody `StackSnapshotCallback` funkcja raz na klatkę zarządzanego, lub raz na przebieg niezarządzane ramek. Jeśli `StackSnapshotCallback` nosi nazwę dla przebiegu niezarządzane ramek, profiler może używać kontekstu rejestru (odwołuje `context` parametru) do wykonania własną stosów niezarządzane. W tym przypadku Win32 `CONTEXT` struktury reprezentuje stan Procesora najbardziej ostatnio wciśnięcia ramki w ramach Uruchom niezarządzane ramki. Mimo że Win32 `CONTEXT` struktura zawiera wartości dla wszystkich rejestrów, należy polegać wyłącznie na wartości rejestru wskaźnik stosu, rejestr wskaźnika ramki, rejestr wskaźnika instrukcji i nieulotnej, (tj. zachowane) rejestruje liczbę całkowitą.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [DoStackSnapshot, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
