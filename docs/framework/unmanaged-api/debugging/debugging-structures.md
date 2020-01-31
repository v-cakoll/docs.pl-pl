---
title: Struktury debugowania
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: a18094fb2621478dbdb4bbf672df436234112ed0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793759"
---
# <a name="debugging-structures"></a>Struktury debugowania

W tej sekcji opisano niezarządzane struktury używane przez interfejs API debugowania.

## <a name="in-this-section"></a>W tej sekcji
 [Struktura CLRDATA_ADDRESS_RANGE](clrdata-address-range-structure.md) Definiuje zakres adresów.

 [Struktura CLRDATA_IL_ADDRESS_MAP](clrdata-il-address-map-structure.md) Definiuje mapowanie IL to Address

 [Struktura CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) Definiuje wersję produktu środowiska uruchomieniowego języka wspólnego (CLR) do celów debugowania.

 [CodeChunkInfo —, struktura](codechunkinfo-structure.md) Reprezentuje pojedynczy fragment kodu w pamięci.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku.

 [Struktura COR_ARRAY_LAYOUT](cor-array-layout-structure.md) Zawiera informacje o układzie obiektu tablicy w pamięci.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Zawiera informacje o przesunięciu dla zakresu kodu.

 [Struktura COR_FIELD](cor-field-structure.md) Zawiera informacje dotyczące pola w obiekcie.

 [Struktura COR_GC_REFERENCE](cor-gc-reference-structure.md) Zawiera informacje o obiekcie, który ma zostać pobrany do pamięci podręcznej.

 [Struktura COR_HEAPINFO](cor-heapinfo-structure.md) Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne

 [Struktura COR_HEAPOBJECT](cor-heapobject-structure.md) Zawiera informacje o obiekcie na zarządzanym stosie.

 [COR_IL_MAP](cor-il-map-structure.md) Określa zmiany w względnym przesunięciu funkcji.

 [Struktura COR_SEGMENT](cor-segment-structure.md) Zawiera informacje o regionie pamięci w zarządzanym stosie.

 [Struktura COR_TYPEID](cor-typeid-structure.md) Zawiera identyfikator typu.

 [Struktura COR_TYPE_LAYOUT](cor-type-layout-structure.md) Zawiera informacje na temat układu obiektu w pamięci.

 [COR_VERSION](cor-version-structure.md) Przechowuje numer standardowej wersji 4-częściowej środowiska uruchomieniowego języka wspólnego.

 [CorDebugBlockingObject, struktura](cordebugblockingobject-structure.md) Definiuje obiekt, który blokuje wątek i powód, dla którego wątek jest zablokowany.

 [CorDebugEHClause, struktura](cordebugehclause-structure.md) Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu języka pośredniego (IL).

 [CorDebugExceptionObjectStackFrame —, struktura](cordebugexceptionobjectstackframe-structure.md) Reprezentuje informacje o ramce stosu z obiektu Exception.

 [CorDebugGuidToTypeMapping —, struktura](cordebugguidtotypemapping-structure.md) Mapuje identyfikator GUID środowisko wykonawcze systemu Windows na odpowiedni obiekt [ICorDebugType](icordebugtype-interface.md) .

 [DacpGetModuleAddress, struktura](dacpgetmoduleaddress-structure.md) Definiuje kontener dla żądania adresu modułu.

 [DacpMethodDescData, struktura](dacpmethoddescdata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym metody.

 [DacpModuleData, struktura](dacpmoduledata-structure.md) Definiuje bufor transportu dla informacji o środowisku uruchomieniowym modułu.

 [DacpReJitData, struktura](dacprejitdata-structure.md) Definiuje podstawowe informacje o danej metodzie Instrumentacji.

 [Struktura StackTrace_SimpleContext](stacktrace-simplecontext-structure.md) Udostępnia prosty kontekst, który może być używany zamiast pełnej struktury `CONTEXT`.

## <a name="related-sections"></a>Sekcje pokrewne

 [Klasy coclass debugowania](debugging-coclasses.md)

 [Debugowanie, interfejsy](debugging-interfaces.md)

 [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)

 [Debugowanie, wyliczenia](debugging-enumerations.md)

 [Debugowanie](index.md)
