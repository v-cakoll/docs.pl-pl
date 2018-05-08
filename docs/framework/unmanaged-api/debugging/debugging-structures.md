---
title: Struktury debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c7415920d34fc231bf82dd00199c7e01eec7a73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-structures"></a>Struktury debugowania
W tej sekcji opisano niezarządzane struktury, których używa interfejsu API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_VERSION, struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.  
  
 [CodeChunkInfo, struktura1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Reprezentuje pojedynczy fragmentu kodu w pamięci.  
  
 [CorDebugBlockingObject, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Definiuje obiekt, który blokuje wątku i przyczyny, dlaczego wątek jest zablokowany.  
  
 [CorDebugEHClause, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Reprezentuje wyjątek klauzuli (EH) dla danego elementu języku pośrednim (IL).  
  
 [CorDebugExceptionObjectStackFrame, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Reprezentuje stosu ramki informacji z obiektu wyjątku.  
  
 [CorDebugExceptionObjectStackFrame, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID na odpowiednie [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) obiektu.  
  
 COR_ACTIVE_FUNCTION —  
 Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach wątku.  
  
 [COR_ARRAY_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Zawiera informacje o układzie tablicy obiektów w pamięci.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP —  
 Zawiera przesunięcia, które są używane do mapowania kodu natywnego kodu języka pośredniego (MSIL) firmy Microsoft.  
  
 COR_DEBUG_STEP_RANGE  
 Zawiera informacje przesunięcia zakresu kodu.  
  
 [COR_FIELD, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Zawiera informacje dotyczące pola w obiekcie.  
  
 [COR_GC_REFERENCE, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Zawiera informacje dotyczące obiektu, który ma być zbierane z pamięci.  
  
 [COR_HEAPINFO, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Ogólne informacje dotyczące odzyskiwania pamięci sterty kolekcji, także wyliczalny.  
  
 [COR_HEAPOBJECT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Zawiera informacje dotyczące obiektów na stercie zarządzanej.  
  
 COR_IL_MAP  
 Określa przesunięcie względną funkcji zmiany.  
  
 [COR_SEGMENT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Zawiera informacje na temat obszar pamięci sterty zarządzanej.  
  
 [COR_TYPEID, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Zawiera identyfikator typu.  
  
 [COR_TYPE_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Zawiera informacje o układzie obiektu w pamięci.  
  
 COR_VERSION —  
 Przechowuje numer wersji czteroczęściową standardowe środowisko uruchomieniowe języka wspólnego.  
  
 [StackTrace_SimpleContext, struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Udostępnia prosty kontekstu, którego można użyć zamiast pełnej `CONTEXT` struktury.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
