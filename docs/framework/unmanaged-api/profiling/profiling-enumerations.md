---
title: Profilowanie — Wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868138"
---
# <a name="profiling-enumerations"></a>Profilowanie — Wyliczenia
W tej sekcji opisano niezarządzane wyliczenia, które są używane przez interfejs API profilowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [COR_PRF_CLAUSE_TYPE, wyliczenie](cor-prf-clause-type-enumeration.md)  
 Wskazuje typ klauzuli wyjątku, który został właśnie wprowadzony lub pozostawiony w kodzie.  
  
 [COR_PRF_CODEGEN_FLAGS, wyliczenie](cor-prf-codegen-flags-enumeration.md)  
 Definiuje flagi generowania kodu, które można ustawić za pomocą metody [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
 [COR_PRF_FINALIZER_FLAGS, wyliczenie](cor-prf-finalizer-flags-enumeration.md)  
 Opisuje finalizator dla obiektu.  
  
 [COR_PRF_GC_GENERATION, wyliczenie](cor-prf-gc-generation-enumeration.md)  
 Identyfikuje generowanie wyrzucania elementów bezużytecznych.  
  
 [COR_PRF_GC_REASON, wyliczenie](cor-prf-gc-reason-enumeration.md)  
 Wskazuje przyczynę wyrzucania elementów bezużytecznych.  
  
 [COR_PRF_GC_ROOT_FLAGS, wyliczenie](cor-prf-gc-root-flags-enumeration.md)  
 Wskazuje właściwości elementu głównego modułu wyrzucania elementów bezużytecznych.  
  
 [COR_PRF_GC_ROOT_KIND, wyliczenie](cor-prf-gc-root-kind-enumeration.md)  
 Wskazuje rodzaj elementu głównego modułu wyrzucania elementów bezużytecznych, który jest udostępniany przez wywołanie zwrotne [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) .  
  
 [Wyliczenie COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)  
 Oferuje flagi oprócz tych, które znajdują się w wyliczeniu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) , który profiler może określić do metody [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) podczas ładowania.  
  
 [COR_PRF_JIT_CACHE, wyliczenie](cor-prf-jit-cache-enumeration.md)  
 Wskazuje wynik funkcji wyszukiwania w pamięci podręcznej.  
  
 [COR_PRF_MISC, wyliczenie](cor-prf-misc-enumeration.md)  
 Zawiera wartości stałe, które określają identyfikatory specjalne.  
  
 [COR_PRF_MODULE_FLAGS, wyliczenie](cor-prf-module-flags-enumeration.md)  
 Określa właściwości modułu.  
  
 [COR_PRF_MONITOR, wyliczenie](cor-prf-monitor-enumeration.md)  
 Zawiera wartości, które są używane do określania zachowania, możliwości lub zdarzeń, do których profiler chce subskrybować.  
  
 [COR_PRF_RUNTIME_TYPE, wyliczenie](cor-prf-runtime-type-enumeration.md)  
 Zawiera wartości wskazujące wersję środowiska uruchomieniowego języka wspólnego.  
  
 [COR_PRF_SNAPSHOT_INFO, wyliczenie](cor-prf-snapshot-info-enumeration.md)  
 Określa ilość danych, które mają zostać przekazane z migawki stosu w każdym wywołaniu funkcji `StackSnapshotCallback` profilera.  
  
 [COR_PRF_STATIC_TYPE, wyliczenie](cor-prf-static-type-enumeration.md)  
 Wskazuje, czy pole jest statyczne i, jeśli tak, statyczna jakość stosowana do pola.  
  
 [COR_PRF_SUSPEND_REASON, wyliczenie](cor-prf-suspend-reason-enumeration.md)  
 Wskazuje przyczynę wstrzymania środowiska uruchomieniowego.  
  
 [COR_PRF_TRANSITION_REASON, wyliczenie](cor-prf-transition-reason-enumeration.md)  
 Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](profiling-overview.md)  
  
 [Interfejsy profilowania](profiling-interfaces.md)  
  
 [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)  
  
 [Profiling — struktury](profiling-structures.md)
