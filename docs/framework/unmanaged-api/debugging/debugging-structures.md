---
title: Struktury debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 05a321d5025f03d6a0378b462178bf06c0291f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123033"
---
# <a name="debugging-structures"></a>Struktury debugowania

W tej sekcji opisano niezarządzane struktury używane przez interfejs API debugowania.

## <a name="in-this-section"></a>W tej sekcji
 [CLRDATA_ADDRESS_RANGE, struktura](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Definiuje zakres adresów.

 [CLRDATA_IL_ADDRESS_MAP, struktura](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Definiuje mapowanie IL to Address

 [CLR_DEBUGGING_VERSION, struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Definiuje wersję produktu środowiska uruchomieniowego języka wspólnego (CLR) do celów debugowania.

 [CodeChunkInfo —, struktura](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Reprezentuje pojedynczy fragment kodu w pamięci.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku.

 [COR_ARRAY_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Zawiera informacje o układzie obiektu tablicy w pamięci.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Zawiera informacje o przesunięciu dla zakresu kodu.

 [COR_FIELD, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Zawiera informacje dotyczące pola w obiekcie.

 [COR_GC_REFERENCE, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Zawiera informacje o obiekcie, który ma zostać pobrany do pamięci podręcznej.

 [COR_HEAPINFO, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne

 [COR_HEAPOBJECT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Zawiera informacje o obiekcie na zarządzanym stosie.

 [COR_IL_MAP](cor-il-map-structure.md) Określa zmiany w względnym przesunięciu funkcji.

 [COR_SEGMENT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Zawiera informacje o regionie pamięci w zarządzanym stosie.

 [COR_TYPEID, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Zawiera identyfikator typu.

 [COR_TYPE_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Zawiera informacje na temat układu obiektu w pamięci.

 [COR_VERSION](cor-version-structure.md) Przechowuje numer standardowej wersji 4-częściowej środowiska uruchomieniowego języka wspólnego.

 [CorDebugBlockingObject, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Definiuje obiekt, który blokuje wątek i powód, dla którego wątek jest zablokowany.

 [CorDebugEHClause, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu języka pośredniego (IL).

 [CorDebugExceptionObjectStackFrame —, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Reprezentuje informacje o ramce stosu z obiektu Exception.

 [CorDebugGuidToTypeMapping —, struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Mapuje identyfikator GUID środowisko wykonawcze systemu Windows na odpowiedni obiekt [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) .

 [DacpGetModuleAddress, struktura](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Definiuje kontener dla żądania adresu modułu.

 [DacpMethodDescData, struktura](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym metody.

 [DacpModuleData, struktura](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym modułu.

 [DacpReJitData, struktura](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Definiuje podstawowe informacje o danej metodzie Instrumentacji.

 [StackTrace_SimpleContext, struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Udostępnia prosty kontekst, który może być używany zamiast pełnej struktury `CONTEXT`.

## <a name="related-sections"></a>Sekcje pokrewne

 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
