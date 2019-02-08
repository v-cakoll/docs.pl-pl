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
ms.openlocfilehash: 18bf03fee1a95c898e8273fa839e41a86b2d1c32
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828374"
---
# <a name="debugging-structures"></a>Struktury debugowania
W tej sekcji opisano niezarządzane struktury, których używa interfejsu API debugowania.

## <a name="in-this-section"></a>W tej sekcji
 [Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definiuje zakres adresów.

 [Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definiuje języka Pośredniego do mapowania adresu

 [Clr_debugging_version — struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.

 [CodeChunkInfo, struktura1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) reprezentuje jeden fragment kodu w pamięci.

 [Cor_active_function —](cor-active-function-structure.md) zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach w wątku.

 [Cor_array_layout — struktury](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) informacje dotyczące układu tablicy obiektów w pamięci.

 [Cor_debug_il_to_native_map —](cor-debug-il-to-native-map-structure.md) zawiera przesunięcia, które są używane do mapowania języka Microsoft intermediate language (MSIL) kod do kodu macierzystego.

 [Cor_debug_step_range —](cor-debug-step-range-structure.md) zawiera informacje o przesunięciu w zakresie kodu.

 [Cor_field — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) informacje na temat pole w obiekcie.

 [Cor_gc_reference — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) zawiera informacje dotyczące obiektu, który ma być zebranych elementów bezużytecznych.

 [Cor_heapinfo — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalna.

 [Cor_heapobject — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) zawiera informacje dotyczące obiektu na stosie zarządzanym.

 [Cor_il_map —](cor-il-map-structure.md) określa zmian w przesunięcie względne funkcji.

 [Cor_segment — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) zawiera informacje o region pamięci w stosie zarządzanym.

 [Cor_typeid — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) zawiera identyfikator typu.

 [Cor_type_layout — struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) informacje dotyczące układu obiektu w pamięci.

 [Cor_version —](cor-version-structure.md) przechowuje standardowe Czteroczęściowy numer środowiska uruchomieniowego języka wspólnego.

 [Cordebugblockingobject — struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) definiuje obiekt, który blokuje wątek i przyczyny, dlaczego wątek jest blokowany.

 [Struktura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) reprezentuje klauzuli obsługi (EH) wyjątek dla danego języka pośredniego (IL).

 [Cordebugexceptionobjectstackframe — struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) reprezentuje stosu ramki informacje z obiekt wyjątku.

 [Cordebugguidtotypemapping — struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] identyfikator GUID służący do odpowiadającymi mu dostawcami [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) obiektu.

 [Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definiuje kontener dla żądania adres modułu.

 [Struktura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) definiuje bufora transportu dla metody środowiska uruchomieniowego informacje.

 [Struktura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) definiuje bufora transportu dla informacje czasu wykonywania modułu.

 [Struktura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) określa podstawowe informacje dotyczące danej metody Instrumentacji profilera.

 [Stacktrace_simplecontext — struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) zapewnia proste kontekst, który można użyć zamiast pełnego `CONTEXT` struktury.



## <a name="related-sections"></a>Sekcje pokrewne
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
