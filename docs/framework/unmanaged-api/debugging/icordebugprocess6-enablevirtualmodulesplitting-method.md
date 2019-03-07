---
title: Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6c2a9c806b70ab33f68e3213d82ed96aca47d62
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484202"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
Włącza lub wyłącza wirtualnego modułu dzielenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true` Aby włączyć wirtualny moduł dzielenia; `false` go wyłączyć.  
  
## <a name="remarks"></a>Uwagi  
 Wirtualny moduł dzielenia powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) do rozpoznawania modułów, które zostały scalone razem podczas kompilacji, przetwarzania i prezentować je jako grupę oddzielnych modułów, a nie w pojedynczym module dużych. W ten sposób zmienia zachowanie różnych [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod opisanych poniżej.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
 Ta metoda może być wywoływana i wartość `enableSplitting` można zmienić w dowolnym momencie. Nie powoduje zmiany funkcjonalności stanowych w [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiektów innych niż zmiany zachowania metody wymienionej w [niezarządzanych API debugowania i wirtualnych modułu dzielenia](#APIs) sekcja w tym czasie, gdy są wywoływane. Korzystanie z wirtualnych modułów spowodować zmniejszenie wydajności podczas wywoływania jednej z tych metod. Ponadto znaczące wewnątrzpamięciowa pamięć podręczna metadanych zwirtualizowanego może być wymagane do poprawnego zaimplementowania [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsów API i te pamięci podręczne mogą zostać zachowane, nawet po zakończeniu podziału wirtualnego modułu została wyłączona.  
  
## <a name="terminology"></a>Terminologia  
 Podczas opisywania wirtualnego modułu dzielenia, są używane następujące terminy:  
  
 Moduły kontenera lub kontenerów  
 Moduły agregacji.  
  
 moduły podrzędne lub moduły wirtualnej  
 Znaleziono modułów w kontenerze.  
  
 regularne modułów  
 Moduły, które nie zostały scalone w czasie kompilacji. Są one modułów kontenera ani modułów podrzędnych.  
  
 Moduły kontenera i moduły podrzędne są reprezentowane przez obiekty interfejsu ICorDebugModule. Jednak zachowanie interfejs jest nieco inne w każdym przypadku jako \<x-ref do sekcji > sekcji opisano.  
  
## <a name="modules-and-assemblies"></a>Moduły i zestawy  
 Zestawy wielu modułu nie są obsługiwane dla zestawu Scalanie scenariuszy, więc istnieje bezpośredni związek pomiędzy modułu i zestawu. Każdy obiekt ICorDebugModule, niezależnie od tego, czy reprezentuje modułu kontenera lub moduł podrzędny ma odpowiedni obiekt ICorDebugAssembly. [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metoda konwertuje z modułu do zestawu. Do mapowania w innym kierunku [ICorDebugAssembly::EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) metoda wylicza tylko 1 modułu. Ponieważ zestaw i moduł formularzu parą ściśle powiązanych w tym przypadku zestaw warunków i moduł stają się większości wymienne.  
  
## <a name="behavioral-differences"></a>Różnice w zachowaniu  
 Moduły kontenera mają następujące zachowania i cechy:  
  
-   Ich metadanych dla wszystkich modułów podrzędnych składowych są scalane.  
  
-   Może być zniekształcone nazwy typu.  
  
-   [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda zwraca ścieżkę do modułu na dysku.  
  
-   [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda zwraca rozmiar tego obrazu.  
  
-   Metoda ICorDebugAssembly3.EnumerateContainedAssemblies Wyświetla listę modułów podrzędnych.  
  
-   Metoda ICorDebugAssembly3.GetContainerAssembly zwraca `S_FALSE`.  
  
 Moduły podrzędne mają następujące zachowania i cechy:  
  
-   Mają one ograniczonym zestawie metadanych, który odpowiada ich oryginalnego zestawu, która została scalona.  
  
-   Nie są zniekształcone nazwy metadanych.  
  
-   Tokeny metadanych to mało prawdopodobne, aby dopasować tokenów w oryginalnych, zanim została scalona w procesie kompilacji.  
  
-   [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda zwraca nazwę zestawu, nie ścieżka do pliku.  
  
-   [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda zwraca oryginalnego rozmiaru obrazu niescalone.  
  
-   Metoda ICorDebugModule3.EnumerateContainedAssemblies zwraca `S_FALSE`.  
  
-   Metoda ICorDebugAssembly3.GetContainerAssembly zwraca zawierającej moduł.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfejsy pobrane z modułów  
 Różne interfejsy, można utworzyć lub pobrać z modułów. Oto niektóre poprawki:  
  
-   Obiekt ICorDebugClass, który jest zwracany przez [ICorDebugModule::GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) metody.  
  
-   Obiekt ICorDebugAssembly, który jest zwracany przez [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metody.  
  
 Te obiekty są zawsze są buforowane przez [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), i będzie miał taką samą tożsamość wskaźnika, niezależnie od tego, czy zostały utworzone lub odpytywane modułu kontenera lub modułu podrzędnego. Moduł podrzędny zawiera widoku filtrowanego znajdującego się tych buforowanych obiektów nie oddzielnych pamięci podręcznej przy użyciu własnej kopii.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Wirtualny moduł dzielenia i niezarządzane interfejsy API debugowania  
 W poniższej tabeli przedstawiono sposób wirtualny moduł dzielenie ma wpływ na zachowanie inne metody w interfejsie API debugowania niezarządzanego.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Zwraca moduł podrzędnych, których ta funkcja została pierwotnie zdefiniowana w|Zwraca moduł kontenera, który zostały scalone z tej funkcji|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Zwraca podrzędny moduł, który ta klasa została pierwotnie zdefiniowana w.|Zwraca moduł kontenera, który zostały scalone z tej klasy.|  
|ICorDebugModuleDebugEvent::GetModule|Zwraca modułu kontenera, który został załadowany. Moduły podrzędne nie są podane zdarzeń ładowania, niezależnie od tego ustawienia.|Zwraca modułu kontenera, który został załadowany.|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Zwraca listę podzespołów i regularnego zestawy; Brak zestawów kontenera są uwzględniane. **Uwaga:**  Jeśli każdy zespół kontenera jest Brak symboli, żaden z jej podzespołów będzie wyliczane. Każdy zespół regularne brakuje symboli, może lub nie można wyliczyć.|Zwraca listę zestawów kontenera i regularnego zestawy; nie podzespołów są uwzględniane. **Uwaga:**  Każdy zespół regularne brakuje symboli, może lub nie można wyliczyć.|  
|[ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (odnosząc się do tylko kod IL)|Zwraca IL, które będą obowiązywać w obrazie scalania wstępnego zestawu. W szczególności wszystkie tokeny metadanych wbudowane poprawnie będzie TypeRef lub MemberRef tokenów gdy typy są określone nie są zdefiniowane w module wirtualnych zawierających IL. Te tokeny TypeRef lub MemberRef można wyszukiwać [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) obiektu dla odpowiedniego obiektu ICorDebugModule wirtualnego.|Zwraca obraz po scalania zestawów IL.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugProcess6, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
