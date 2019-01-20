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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415328"
---
# <a name="debugging-structures"></a>Struktury debugowania
W tej sekcji opisano niezarządzane struktury, których używa interfejsu API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_VERSION, struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.  
  
 [CodeChunkInfo, struktura1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Reprezentuje jeden fragment kodu w pamięci.  
  
 [CorDebugBlockingObject, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Definiuje obiekt, który blokuje wątek i przyczyny, dlaczego wątek jest blokowany.  
  
 [CorDebugEHClause, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Reprezentuje wyjątek obsługi klauzuli (EH) dla danego języka pośredniego (IL).  
  
 [CorDebugExceptionObjectStackFrame, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Reprezentuje stosu ramki informacje z obiekt wyjątku.  
  
 [CorDebugExceptionObjectStackFrame, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID służący do odpowiadającymi mu dostawcami [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) obiektu.  
  
 COR_ACTIVE_FUNCTION  
 Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach w wątku.  
  
 [COR_ARRAY_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Informacje dotyczące układu obiektu tablicowego w pamięci.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP  
 Zawiera przesunięcia, które są używane do mapowania kod intermediate language (MSIL) firmy Microsoft do kodu macierzystego.  
  
 COR_DEBUG_STEP_RANGE  
 Zawiera informacje przesunięcia w zakresie kodu.  
  
 [COR_FIELD, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Zawiera informacje dotyczące pól w obiekcie.  
  
 [COR_GC_REFERENCE, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Zawiera informacje dotyczące obiektu, który ma być zebranych elementów bezużytecznych.  
  
 [COR_HEAPINFO, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalna.  
  
 [COR_HEAPOBJECT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Zawiera informacje dotyczące obiektu na stosie zarządzanym.  
  
 COR_IL_MAP  
 Określa przesunięcie względne funkcji zmiany.  
  
 [COR_SEGMENT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Zawiera informacje o region pamięci w stosie zarządzanym.  
  
 [COR_TYPEID, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Zawiera identyfikator typu.  
  
 [COR_TYPE_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Informacje dotyczące układu obiektu w pamięci.  
  
 COR_VERSION  
 Przechowuje standardowe Czteroczęściowy numer środowiska uruchomieniowego języka wspólnego.  
  
 [StackTrace_SimpleContext, struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Udostępnia prosty kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.

 [Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definiuje zakres adresów.
 
 [Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definiuje języka Pośredniego do mapowania adresu
 
 [Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definiuje kontener dla żądania adres modułu.

  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
