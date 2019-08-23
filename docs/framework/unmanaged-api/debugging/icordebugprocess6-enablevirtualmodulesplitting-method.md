---
title: Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bd06dd3f58a1f74fbdb5ec61c4896f5c1696856
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931057"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>Metoda ICorDebugProcess6::EnableVirtualModuleSplitting
Włącza lub wyłącza dzielenie modułu wirtualnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true`Aby włączyć dzielenie modułu wirtualnego; `false` aby go wyłączyć.  
  
## <a name="remarks"></a>Uwagi  
 Dzielenie modułu wirtualnego powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozpoznaje moduły, które zostały scalone podczas procesu kompilacji i są prezentowane jako Grupa oddzielnych modułów, a nie do pojedynczego dużego modułu. Spowoduje to zmianę zachowania różnych metod [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) opisanych poniżej.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
 Tę metodę można wywołać, a wartość `enableSplitting` można zmienić w dowolnym momencie. Nie powoduje żadnych zmian w działaniu stanowym w obiekcie [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , innych niż zmiana zachowania metod wymienionych w sekcji [dzielenie modułu wirtualnego i niezarządzane interfejsy API debugowania](#APIs) w momencie ich wywołania. Użycie modułów wirtualnych powoduje spadek wydajności podczas wywoływania tych metod. Ponadto w celu prawidłowego zaimplementowania interfejsów API [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) może być wymagane znaczne buforowanie w pamięci, a te pamięci podręczne mogą być przechowywane nawet po wyłączeniu dzielenia modułu wirtualnego.  
  
## <a name="terminology"></a>Terminologia  
 Poniższe terminy są używane podczas opisywania podziału modułu wirtualnego:  
  
 Moduły kontenera lub kontenery  
 Moduły agregujące.  
  
 moduły podrzędne lub moduły wirtualne  
 Moduły, które znajdują się w kontenerze.  
  
 regularne moduły  
 Moduły, które nie zostały scalone w czasie kompilacji. Nie są to moduły kontenera ani moduły podrzędne.  
  
 Moduły kontenera i moduły podrzędne są reprezentowane przez obiekty interfejsu ICorDebugModule. Jednak zachowanie interfejsu jest nieco inne w każdym przypadku, zgodnie z opisem w \<sekcji x-ref do sekcji >.  
  
## <a name="modules-and-assemblies"></a>Moduły i zestawy  
 Zestawy obejmujące wiele modułów nie są obsługiwane w scenariuszach scalania zestawów, dlatego istnieje relacja jeden do jednego między modułem a zestawem. Każdy obiekt ICorDebugModule, niezależnie od tego, czy reprezentuje on moduł kontenera lub moduł podrzędny, ma odpowiedni obiekt ICorDebugAssembly. Metoda [ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) konwertuje moduł do zestawu. Aby zamapować w innym kierunku, Metoda [ICorDebugAssembly:: EnumerateModules —](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) wylicza tylko jeden moduł. Ponieważ zestaw i moduł tworzą ściśle sprzężoną parę w tym przypadku, zestaw terminów i moduł stają się w dużym stopniu zamienne.  
  
## <a name="behavioral-differences"></a>Różnice w zachowaniu  
 Moduły kontenera mają następujące zachowania i cechy:  
  
- Ich metadane dla wszystkich modułów podrzędnych są scalane ze sobą.  
  
- Ich nazwy typów mogą być zniekształcona.  
  
- Metoda [ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) zwraca ścieżkę do modułu na dysku.  
  
- Metoda [ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) zwraca rozmiar tego obrazu.  
  
- Metoda ICorDebugAssembly3. EnumerateContainedAssemblies Wyświetla listę modułów podrzędnych.  
  
- Metoda ICorDebugAssembly3. GetContainerAssembly zwraca wartość `S_FALSE`.  
  
 Moduły podrzędne mają następujące zachowania i cechy:  
  
- Mają zredukowany zestaw metadanych, który odnosi się tylko do oryginalnego zestawu, który został scalony.  
  
- Nazwy metadanych nie są zniekształcona.  
  
- Tokeny metadanych nie są prawdopodobnie zgodne z tokenami w oryginalnym zestawie, zanim zostały scalone w procesie kompilacji.  
  
- Metoda [ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) zwraca nazwę zestawu, a nie ścieżkę do pliku.  
  
- Metoda [ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) zwraca oryginalny Niescalony rozmiar obrazu.  
  
- Metoda ICorDebugModule3. EnumerateContainedAssemblies zwraca wartość `S_FALSE`.  
  
- Metoda ICorDebugAssembly3. GetContainerAssembly zwraca moduł zawierający.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfejsy pobrane z modułów  
 Różne interfejsy mogą być tworzone lub pobierane z modułów. Oto niektóre poprawki:  
  
- Obiekt ICorDebugClass, który jest zwracany przez metodę [ICorDebugModule:: GetClassFromToken —](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) .  
  
- Obiekt ICorDebugAssembly, który jest zwracany przez metodę [ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) .  
  
 Te obiekty są zawsze buforowane przez [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)i będą miały taką samą tożsamość wskaźnika, niezależnie od tego, czy zostały utworzone, czy zapytania z modułu kontenera lub modułu podrzędnego. Moduł podrzędny zapewnia przefiltrowany widok tych obiektów w pamięci podręcznej, a nie osobną pamięć podręczną ze swoimi kopiami.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Dzielenie modułu wirtualnego i niezarządzane interfejsy API debugowania  
 W poniższej tabeli przedstawiono sposób dzielenia modułu wirtualnego na zachowanie innych metod w niezarządzanym interfejsie API debugowania.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Zwraca moduł podrzędny, w którym ta funkcja została pierwotnie zdefiniowana.|Zwraca moduł kontenera, do którego ta funkcja została scalona|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Zwraca moduł podrzędny, w którym ta klasa została pierwotnie zdefiniowana.|Zwraca moduł kontenera, do którego ta klasa została scalona.|  
|ICorDebugModuleDebugEvent:: GetModule|Zwraca moduł kontenera, który został załadowany. Moduły podrzędne nie otrzymują zdarzeń ładowania, niezależnie od tego ustawienia.|Zwraca moduł kontenera, który został załadowany.|  
|[ICorDebugAppDomain:: EnumerateAssemblies —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Zwraca listę podzespołów i zwykłych zestawów; nie dołączono żadnych zestawów kontenerów. **Uwaga:**  Jeśli w dowolnym zestawie kontenerów brakuje symboli, żaden z jej podzespołów nie zostanie wyliczony. Jeśli w dowolnym z zestawów zwykłych brakuje symboli, może ona być wyliczona lub nie można jej wyliczyć.|Zwraca listę zestawów kontenerów i zwykłych zestawów; żadne podzestawy nie są uwzględniane. **Uwaga:**  Jeśli w dowolnym z zestawów zwykłych brakuje symboli, może ona być wyliczona lub nie można jej wyliczyć.|  
|[ICorDebugCode:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (w przypadku odwoływania się tylko do kodu IL)|Zwraca IL, który byłby prawidłowy w obrazie zestawu poprzedzającego scalenie. W każdym przypadku tokeny wbudowanej metadanych będą poprawnie mieć tokeny TypeRef lub MemberRef, gdy typy, do których się odwołuje, nie są zdefiniowane w module wirtualnym zawierającym IL. Te tokeny TypeRef lub MemberRef mogą być wyszukiwane w obiekcie [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) dla odpowiadającego wirtualnego obiektu ICorDebugModule.|Zwraca IL w obrazie zestawu po scaleniu.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess6, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
