---
title: Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178570"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
Włącza lub wyłącza dzielenie modułów wirtualnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true`, aby włączyć dzielenie modułu wirtualnego; `false` , aby go wyłączyć.  
  
## <a name="remarks"></a>Uwagi  
 Dzielenie modułów wirtualnych powoduje, że [ICorDebug](icordebug-interface.md) rozpoznaje moduły, które zostały scalone podczas procesu kompilacji i przedstawia je jako grupę oddzielnych modułów, a nie jeden duży moduł. W ten sposób zmienia zachowanie różnych metod [ICorDebug](icordebug-interface.md) opisane poniżej.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
 Ta metoda może być wywołana i wartość można zmienić `enableSplitting` w dowolnym momencie. Nie powoduje żadnych zmian funkcjonalnych stanowych w obiekcie [ICorDebug,](icordebug-interface.md) inne niż zmiana zachowania metod wymienionych w [modułu wirtualnego podziału i niezarządzanych debugowania interfejsów API](#APIs) sekcji w czasie, gdy są wywoływane. Przy użyciu modułów wirtualnych wiąże się z karą wydajności podczas wywoływania tych metod. Ponadto do prawidłowego zaimplementowania interfejsów API [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) może być wymagane istotne buforowanie zwirtualizowanych metadanych w pamięci podręcznej, a te pamięci podręczne mogą być zachowywane nawet po wyłączeniu podziału modułu wirtualnego.  
  
## <a name="terminology"></a>Terminologia  
 Następujące terminy są używane przy opisywaniu podziału modułu wirtualnego:  
  
 moduły kontenerowe lub kontenery  
 Moduły agregowane.  
  
 podkomisjowe lub moduły wirtualne  
 Moduły znalezione w kontenerze.  
  
 moduły regularne  
 Moduły, które nie zostały scalone w czasie kompilacji. Nie są to ani moduły kontenerowe, ani podkomisarz.  
  
 Moduły kontenerów i podmoduły są reprezentowane przez obiekty interfejsu ICorDebugModule. Jednak zachowanie interfejsu jest nieco inna w każdym \<przypadku, jak x-ref do sekcji>.  
  
## <a name="modules-and-assemblies"></a>Moduły i zespoły  
 Zestawy wielu modułów nie są obsługiwane dla scenariuszy scalania zestawu, więc istnieje relacja jeden do jednego między modułem a zestawem. Każdy obiekt ICorDebugModule, niezależnie od tego, czy reprezentuje moduł kontenera, czy podmoduł, ma odpowiedni obiekt ICorDebugAssembly. [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) metoda konwertuje z modułu do zestawu. Aby zamapować w innym kierunku, [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) metoda wylicza tylko 1 moduł. Ponieważ montaż i moduł tworzą w tym przypadku szczelnie sprzężona para, terminy złożenia i modułu stają się w dużej mierze wymienne.  
  
## <a name="behavioral-differences"></a>Różnice w zachowaniu  
 Moduły kontenerów mają następujące zachowania i właściwości:  
  
- Ich metadane dla wszystkich pod module składowych są scalane ze sobą.  
  
- Ich nazwy typów mogą być zniekształcone.  
  
- Metoda [ICorDebugModule::GetName](icordebugmodule-getname-method.md) zwraca ścieżkę do modułu na dysku.  
  
- [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) Metoda zwraca rozmiar tego obrazu.  
  
- Metoda ICorDebugAssembly3.EnumerateContainedAssemblies wyświetla listę pod moduleów.  
  
- Metoda ICorDebugAssembly3.GetContainerAssembly `S_FALSE`zwraca .  
  
 Podzepartamy mają następujące zachowania i właściwości:  
  
- Mają one zmniejszony zestaw metadanych, który odpowiada tylko oryginalnego zestawu, który został scalony.  
  
- Nazwy metadanych nie są zniekształcone.  
  
- Tokeny metadanych jest mało prawdopodobne, aby dopasować tokeny w oryginalnym zestawie, zanim został scalony w procesie kompilacji.  
  
- [Metoda ICorDebugModule::GetName](icordebugmodule-getname-method.md) zwraca nazwę zestawu, a nie ścieżkę pliku.  
  
- [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) Metoda zwraca oryginalny rozmiar obrazu niesraszonego.  
  
- Metoda ICorDebugModule3.EnumerateContainedAssemblies `S_FALSE`zwraca .  
  
- Metoda ICorDebugAssembly3.GetContainerAssembly zwraca moduł zawierający.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfejsy pobierane z modułów  
 Różne interfejsy mogą być tworzone lub pobierane z modułów. Oto niektóre poprawki:  
  
- Obiekt ICorDebugClass, który jest zwracany przez [metodę ICorDebugModule::GetClassFromToken.](icordebugmodule-getclassfromtoken-method.md)  
  
- Obiekt ICorDebugAssembly, który jest zwracany przez [metodę ICorDebugModule::GetAssembly.](icordebugmodule-getassembly-method.md)  
  
 Obiekty te są zawsze buforowane przez [ICorDebug](icordebug-interface.md)i będą miały tę samą tożsamość wskaźnika, niezależnie od tego, czy zostały utworzone lub zapytane z modułu kontenera lub pod module. Pod module udostępnia filtrowany widok tych obiektów buforowanych, a nie oddzielną pamięć podręczną z własnymi kopiami.  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Dzielenie modułu wirtualnego i niezarządzane debugowanie interfejsów API  
 W poniższej tabeli pokazano, jak dzielenie modułu wirtualnego wpływa na zachowanie innych metod w niezarządzanym debugowaniu interfejsu API.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|Zwraca pod module, który ta funkcja została pierwotnie zdefiniowana w|Zwraca moduł kontenera, z który ta funkcja została scalona|  
|[Klasa ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|Zwraca pod module, w który pierwotnie zdefiniowano tę klasę.|Zwraca moduł kontenera, do który została scalona ta klasa.|  
|ICorDebugModuleDebugEvent::GetModule|Zwraca moduł kontenera, który został załadowany. Pod moduły nie są podane zdarzenia obciążenia, niezależnie od tego ustawienia.|Zwraca moduł kontenera, który został załadowany.|  
|[Domena aplikacji ICorDebugApp::Wyliczajasemblies](icordebugappdomain-enumerateassemblies-method.md)|Zwraca listę podzespołów i zestawów regularnych; nie są uwzględniane żadne zestawy kontenerów. **Uwaga:**  Jeśli w jakimkolwiek zestawie kontenerów brakuje symboli, żaden z jego podzespołów nie zostanie wyliczony. Jeśli dowolny zestaw regularnych brakuje symboli, może lub nie może być wyliczony.|Zwraca listę zestawów kontenerów i zestawów regularnych; nie są uwzględniane żadne podzespołania. **Uwaga:**  Jeśli dowolny zestaw regularnych brakuje symboli, może lub nie może być wyliczony.|  
|[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (tylko w przypadku odwoływania się do kodu IL)|Zwraca IL, który byłby prawidłowy w obrazie złożenia przed scaleniem. W szczególności wszystkie wbudowane tokeny metadanych będą poprawnie TypeRef lub MemberRef tokeny, gdy typy, o których mowa, nie są zdefiniowane w module wirtualnym zawierającym IL. Te tokeny TypeRef lub MemberRef można wyszukać w [obiekcie IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) dla odpowiedniego obiektu wirtualnego ICorDebugModule.|Zwraca il na obrazze złożenia po scaleniu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
