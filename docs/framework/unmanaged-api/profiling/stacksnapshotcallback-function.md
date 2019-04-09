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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 891423661f45a1167d53385e6e0306fb09487278
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198325"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback — Funkcja
Dostarcza informacji na temat każdej zarządzanej ramki i każde uruchomienie niezarządzanych ramek na stosie podczas przeszukiwania stosu jest inicjowane przez profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
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
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Jeśli ta wartość wynosi zero, to wywołanie zwrotne jest uruchomieniu ramek niezarządzane; w przeciwnym razie jest to identyfikator funkcji zarządzanej i jest to wywołanie zwrotne ramki zarządzanej.  
  
 `ip`  
 [in] Wartość wskaźnika instrukcji kodu natywnego w ramce.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` wartość, która odwołuje się do informacji na temat ramki stosu. Ta wartość jest prawidłowa do stosowania tylko podczas tego wywołania zwrotnego.  
  
 `contextSize`  
 [in] Rozmiar `CONTEXT` struktury, która odwołuje się do niej `context` parametru.  
  
 `context`  
 [in] Wskaźnik do systemu Win32 `CONTEXT` strukturę, która reprezentuje stan procesora CPU dla tej ramki.  
  
 `context` Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT przekazano `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Wskaźnik do danych klienta, która jest przekazywana bezpośrednio z `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Uwagi  
 `StackSnapshotCallback` Funkcji jest implementowany przez twórcę profilera. Należy ograniczyć złożoność pracy wykonanej w `StackSnapshotCallback`. Na przykład w przypadku korzystania z `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny, wątek docelowy może być utrzymywanie blokad. Jeśli kodu w ramach `StackSnapshotCallback` wymaga tych samych blokad, zakleszczeń może nastąpić.  
  
 `ICorProfilerInfo2::DoStackSnapshot` Wywołania metody `StackSnapshotCallback` funkcję jeden raz na klatkę zarządzanych lub raz na przebieg niezarządzanych ramek. Jeśli `StackSnapshotCallback` jest wywoływana dla przebiegu niezarządzanych ramek, profiler może użyć kontekstu rejestru (wskazywanym przez `context` parametr) aby wykonać swoje własne niezarządzane stosów. W tym przypadku Win32 `CONTEXT` struktury reprezentuje stan procesora CPU dla najbardziej niedawno wypychanie ramki w ramach wykonywania niezarządzanych ramek. Mimo że Win32 `CONTEXT` struktura zawiera wartości dla wszystkich rejestrów, należy polegać tylko na wartości rejestru wskaźnik stosu, rejestr wskaźnika ramki, rejestr wskaźnika instrukcji i nieulotnej, (które zachowane) rejestruje liczbę całkowitą.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DoStackSnapshot, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
