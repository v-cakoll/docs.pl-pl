---
title: Profilowanie — Wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: bc90743fb348c31bd2f7487c1573ec38a43bd3af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447449"
---
# <a name="profiling-enumerations"></a>Profilowanie — Wyliczenia
W tej sekcji opisano niezarządzane wyliczenia, które są używane przez interfejs API profilowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [COR_PRF_CLAUSE_TYPE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Wskazuje typ klauzuli wyjątku, który został właśnie wprowadzony lub pozostawiony w kodzie.  
  
 [COR_PRF_CODEGEN_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Definiuje flagi generowania kodu, które można ustawić za pomocą metody [ICorProfilerFunctionControl:: SetCodegenFlags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
 [COR_PRF_FINALIZER_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Opisuje finalizator dla obiektu.  
  
 [COR_PRF_GC_GENERATION, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Identyfikuje generowanie wyrzucania elementów bezużytecznych.  
  
 [COR_PRF_GC_REASON, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Wskazuje przyczynę wyrzucania elementów bezużytecznych.  
  
 [COR_PRF_GC_ROOT_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Wskazuje właściwości elementu głównego modułu wyrzucania elementów bezużytecznych.  
  
 [COR_PRF_GC_ROOT_KIND, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Wskazuje rodzaj elementu głównego modułu wyrzucania elementów bezużytecznych, który jest udostępniany przez wywołanie zwrotne [ICorProfilerCallback2:: RootReferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) .  
  
 [Wyliczenie COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Oferuje flagi oprócz tych, które znajdują się w wyliczeniu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) , który profiler może określić do metody [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) podczas ładowania.  
  
 [COR_PRF_JIT_CACHE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Wskazuje wynik funkcji wyszukiwania w pamięci podręcznej.  
  
 [COR_PRF_MISC, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Zawiera wartości stałe, które określają identyfikatory specjalne.  
  
 [COR_PRF_MODULE_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Określa właściwości modułu.  
  
 [COR_PRF_MONITOR, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Zawiera wartości, które są używane do określania zachowania, możliwości lub zdarzeń, do których profiler chce subskrybować.  
  
 [COR_PRF_RUNTIME_TYPE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Zawiera wartości wskazujące wersję środowiska uruchomieniowego języka wspólnego.  
  
 [COR_PRF_SNAPSHOT_INFO, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Określa ilość danych, które mają zostać przekazane z migawki stosu w każdym wywołaniu funkcji `StackSnapshotCallback` profilera.  
  
 [COR_PRF_STATIC_TYPE, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Wskazuje, czy pole jest statyczne i, jeśli tak, statyczna jakość stosowana do pola.  
  
 [COR_PRF_SUSPEND_REASON, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Wskazuje przyczynę wstrzymania środowiska uruchomieniowego.  
  
 [COR_PRF_TRANSITION_REASON, wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
