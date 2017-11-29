---
title: Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6e1f459636f1bb2b3844eebdb98bebd1deb73cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
Włącza lub wyłącza wirtualnego modułu dzielenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true`Aby włączyć wirtualne modułu dzielenia; `false` je wyłączyć.  
  
## <a name="remarks"></a>Uwagi  
 Wirtualne modułu dzielenia przyczyny [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozpoznawanie modułów, które zostały scalone, podczas kompilacji przetwarzania i prezentować je jako grupę oddzielnych modułów zamiast pojedynczy moduł duże. W ten sposób zmienia zachowanie różnych [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod opisanych poniżej.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
 Tę metodę można wywołać i wartość `enableSplitting` można zmienić w dowolnym momencie. Nie powoduje zmiany funkcjonalne stanowe w [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiektu innego niż zmianę zachowania metody wymienione w [niezarządzanych API debugowania i wirtualne modułu dzielenia](#APIs) sekcja w czasie, gdy są wywoływane. Przy użyciu modułów wirtualnych pociągnąć za sobą zmniejszenie wydajności podczas wywoływania metod. Ponadto istotne buforowania w pamięci zwirtualizowanych metadanych może być konieczne prawidłowo zaimplementować [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsów API i te pamięci podręczne mogą zostać zachowane, nawet po wirtualnego modułu dzielenia zostało wyłączone.  
  
## <a name="terminology"></a>Terminologia  
 Poniższe terminy są używane podczas opisywania wirtualnego modułu dzielenia:  
  
 Moduły kontenera lub kontenerów  
 Moduły agregacji.  
  
 moduły podrzędne lub wirtualnych modułów  
 Znaleziono modułów w kontenerze.  
  
 regularne modułów  
 Moduły, które nie zostały scalone w czasie kompilacji. Są one modułów kontenera ani modułów podrzędnych.  
  
 Zarówno modułów kontenera i moduły podrzędne są reprezentowane przez obiekty interfejsu ICorDebugModule. Jednak zachowanie interfejsu różni się nieco w każdym przypadku jako \<x-ref sekcji > sekcji opisano.  
  
## <a name="modules-and-assemblies"></a>Moduły i zestawy  
 Zestawy wielomodułowe nie są obsługiwane dla zestawu Scalanie scenariuszy, więc istnieje relacja jeden do jednego między modułem i zestawu. Każdy obiekt ICorDebugModule, niezależnie od tego, czy reprezentuje modułu kontenera lub modułu podrzędnego, ma odpowiedni obiekt ICorDebugAssembly. [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metoda konwertuje z modułu do zestawu. Aby mapować w innym kierunku [ICorDebugAssembly::EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) metoda wylicza modułu tylko na 1. Ponieważ zestaw i moduł formularzu silnie sprzężonego pary w takim przypadku postanowienia zestaw i moduł stają się większości wymienne.  
  
## <a name="behavioral-differences"></a>Różnice funkcjonalne  
 Kontener moduły mają następujące zachowania i właściwości:  
  
-   Ich metadanych dla wszystkich modułów składowych podrzędne są scalane.  
  
-   Może być zniekształcone nazwy typu.  
  
-   [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda zwraca ścieżkę do modułu na dysku.  
  
-   [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda zwraca rozmiar tego obrazu.  
  
-   Metoda ICorDebugAssembly3.EnumerateContainedAssemblies Wyświetla listę modułów podrzędnych.  
  
-   Zwraca metodę ICorDebugAssembly3.GetContainerAssembly `S_FALSE`.  
  
 Moduły podrzędne mają następujące zachowania i właściwości:  
  
-   Mają one ograniczonego zestawu metadanych, która odnosi się tylko do oryginalnego zestawu, który został scalony.  
  
-   Nazwy metadanych nie są zniekształcone.  
  
-   Tokeny metadanych to mało prawdopodobne, aby dopasować tokenów w oryginalnych, zanim go została scalona w procesie kompilacji.  
  
-   [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda zwraca nazwę zestawu, a nie ścieżkę pliku.  
  
-   [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda zwraca oryginalnego rozmiaru obrazu niescalone.  
  
-   Zwraca metodę ICorDebugModule3.EnumerateContainedAssemblies `S_FALSE`.  
  
-   Metoda ICorDebugAssembly3.GetContainerAssembly zwraca modułu zawierającego.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfejsy pobrane z modułów  
 Wiele interfejsów można utworzyć lub pobrać z modułów. Oto niektóre z nich:  
  
-   ICorDebugClass obiekt, który jest zwracany przez [ICorDebugModule::GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) metody.  
  
-   ICorDebugAssembly obiekt, który jest zwracany przez [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metody.  
  
 Te obiekty są zawsze w pamięci podręcznej [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), i mają one taką samą tożsamość wskaźnika, niezależnie od tego, czy zostały utworzone lub z modułu podrzędnego lub moduł kontenera. Modułu podrzędnego zawiera widok filtrowane tych obiektów pamięci podręcznej nie oddzielnych pamięci podręcznej z własnej kopii.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Wirtualne modułu dzielenia i niezarządzanych API debugowania  
 W poniższej tabeli przedstawiono sposób wirtualnego modułu dzielenia wpływa na działanie innych metod w niezarządzanych API debugowania.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Zwraca podrzędny moduł, który ta funkcja została pierwotnie zdefiniowana w|Zwraca moduł kontenera, który zostały scalone z tej funkcji|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Zwraca podrzędny moduł, który ta klasa została pierwotnie zdefiniowana w.|Zwraca moduł kontenera, który zostały scalone z tej klasy.|  
|ICorDebugModuleDebugEvent::GetModule|Zwraca moduł kontenera, który został załadowany. Moduły podrzędne nie są podane zdarzeń ładowania niezależnie od tego ustawienia.|Zwraca moduł kontenera, który został załadowany.|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Zwraca listę podzespołów i zestawy regularne; uwzględniono żadnych zestawów kontenera. **Uwaga:** Jeśli żadnych zestawów kontenera brakuje symbole, żaden z jego podzespołów będą wyliczane. Jeśli wszystkie regularne zestawu brakuje symbole, może lub nie może wyliczyć.|Zwraca listę zestawów kontenera i zestawy regularne; nie podzespołów są uwzględniane. **Uwaga:** Jeśli żadnych regularne zestawu brakuje symbole, mogą lub nie można wyliczyć.|  
|[ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (odnosząc się do kodu IL tylko)|Zwraca IL, który będzie ważny w obrazie zestawu wstępne scalania. W szczególności tokenów metadanych wbudowanego poprawnie będzie TypeRef lub MemberRef tokenów gdy są określone typy nie są zdefiniowane w module wirtualnych zawierających IL. Tokeny te TypeRef lub MemberRef można przeszukiwać [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) obiektu dla odpowiedniego obiektu ICorDebugModule wirtualnego.|Zwraca obraz po scalania zestawu IL.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
