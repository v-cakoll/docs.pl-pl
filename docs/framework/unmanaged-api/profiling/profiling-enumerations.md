---
title: Profilowanie — Wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996352637f34b0b6c0d12e611a6d9e70ab85230e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757576"
---
# <a name="profiling-enumerations"></a>Profilowanie — Wyliczenia
W tej sekcji opisano niezarządzane wyliczenia, których używa interfejs profilowania API.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [COR_PRF_CLAUSE_TYPE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Wskazuje typ klauzuli wyjątek, który po prostu wprowadzony kod lub po lewej stronie.  
  
 [COR_PRF_CODEGEN_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Określa flagi generowania kodu, które można ustawić za pomocą [icorprofilerfunctioncontrol::setcodegenflags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.  
  
 [COR_PRF_FINALIZER_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 W tym artykule opisano finalizatora obiektu.  
  
 [COR_PRF_GC_GENERATION, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Identyfikuje generacjach wyrzucania.  
  
 [COR_PRF_GC_REASON, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Wskazuje powód, że odbywa się wyrzucanie elementów bezużytecznych.  
  
 [COR_PRF_GC_ROOT_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Określa właściwości głównego modułu zbierającego elementy bezużyteczne.  
  
 [COR_PRF_GC_ROOT_KIND, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Wskazuje rodzaj głównego modułu odśmiecania pamięci, który jest udostępniany przez [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.  
  
 [Wyliczenie COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Zawiera flagi, oprócz tych dostępnych w [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenie, które można określić profiler [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metodą podczas wczytywania.  
  
 [COR_PRF_JIT_CACHE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Wskazuje wynik wyszukiwania funkcję pamięci podręcznej.  
  
 [COR_PRF_MISC, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Zawiera wartości stałych, które określają specjalne identyfikatory.  
  
 [COR_PRF_MODULE_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Określa właściwości modułu.  
  
 [COR_PRF_MONITOR, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Zawiera wartości, które są używane do określania zachowania, funkcji lub zdarzeń do których program profilujący chce subskrypcji.  
  
 [COR_PRF_RUNTIME_TYPE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Zawiera wartości, które wskazują wersję środowiska uruchomieniowego języka wspólnego.  
  
 [COR_PRF_SNAPSHOT_INFO, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Określa, ile danych do przekazania z powrotem przy użyciu migawek w każdym wywołaniu do programu profilującego stosu `StackSnapshotCallback` funkcji.  
  
 [COR_PRF_STATIC_TYPE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Wskazuje, czy pole jest statyczna, a jeśli tak, statycznej jakości, która odnosi się do pola.  
  
 [COR_PRF_SUSPEND_REASON, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Wskazuje powód, że środowisko uruchomieniowe zostało wstrzymane.  
  
 [COR_PRF_TRANSITION_REASON, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub na odwrót.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
