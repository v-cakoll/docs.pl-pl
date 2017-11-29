---
title: "Profilowanie — Wyliczenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e0b539c8e455040cc97f37f75476b0efe796abb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-enumerations"></a>Profilowanie — Wyliczenia
W tej sekcji opisano niezarządzane wyliczenia, które używa interfejsu API profilowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [COR_PRF_CLAUSE_TYPE — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Wskazuje typ klauzuli wyjątek, który właśnie wprowadzony kod lub w lewo.  
  
 [Cor_prf_codegen_flags — wyliczanie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Określa flagi generowania kodu, które można ustawić za pomocą [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) metody.  
  
 [Cor_prf_finalizer_flags — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 W tym artykule opisano finalizatora obiektu.  
  
 [Cor_prf_gc_generation — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Określa Generowanie kolekcji pamięci.  
  
 [COR_PRF_GC_REASON — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Wskazuje Przyczyna występuje wyrzucanie elementów bezużytecznych.  
  
 [Cor_prf_gc_root_flags — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Wskazuje właściwości główny moduł zbierający elementy bezużyteczne.  
  
 [COR_PRF_GC_ROOT_KIND — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Wskazuje typ modułu zbierającego elementy bezużyteczne głównego, który jest udostępniany przez [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.  
  
 [Wyliczenie COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Udostępnia flagi oprócz występujące w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia, które można określić profilera [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody podczas jego ładowania.  
  
 [Cor_prf_jit_cache — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Wskazuje wynik wyszukiwania funkcji pamięci podręcznej.  
  
 [COR_PRF_MISC — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Zawiera stałe wartości, które określają specjalne identyfikatorów.  
  
 [Cor_prf_module_flags — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Określa właściwości modułu.  
  
 [COR_PRF_MONITOR — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Zawiera wartości, które są używane do określania zachowania, funkcji lub zdarzeń do których chce subskrypcji profilera.  
  
 [COR_PRF_RUNTIME_TYPE — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Zawiera wartości, które wskazują wersji środowiska CLR.  
  
 [Cor_prf_snapshot_info — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Określa, ile kopii danych do przekazania z migawki w każdym wywołaniu profilera stosu `StackSnapshotCallback` funkcji.  
  
 [COR_PRF_STATIC_TYPE — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Wskazuje, czy pole jest statyczny, a jeśli tak, statyczne jakości dotyczący pola.  
  
 [COR_PRF_SUSPEND_REASON — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Wskazuje przyczynę zawieszenia środowiska uruchomieniowego.  
  
 [Cor_prf_transition_reason — wyliczenie](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Statyczne funkcje globalne profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Struktury profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
