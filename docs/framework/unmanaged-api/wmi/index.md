---
title: "Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI"
description: "Podsumowuje programu .NET Framework niezarządzanych API usługi WMI i wydajności informacji licznika."
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.date: 11/06/2017
ms.topic: reference
ms.prod: .net-framework
ms.devlang: cpp
ms.workload:
- dotnet
ms.openlocfilehash: c7959d6b6b7bafd728db5a579ff1376e686c5b74
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Instrumentacja zarządzania Windows (WMI) i liczniki wydajności (niezarządzany wykaz interfejsów API)

Liczniki wydajności i .NET Framework WMI niezarządzanego API składa się z zestaw funkcji, które otaczają wywołań [natywnego interfejsu API Instrumentacji zarządzania Windows](https://msdn.microsoft.com/library/aa389276(v=vs.85).aspx). Umożliwia tworzenie narzędzia i biblioteki, w których zarządzanie i monitorowanie komputerów zdalnych.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
Interfejs API zawiera następujące funkcje:

| Funkcja | Opis |
|---------|---------|
| [Funkcja BeingEnumeration](beginenumeration.md) | Resetuje modułu wyliczającego początek wyliczenia właściwości obiektu WMI. |
| [Funkcja BeginMethodEnumeration](beginmethodenumeration.md) |  Rozpoczyna się wyliczenia metod dla obiekt. |
| [Funkcja BlessIWbemServices](blessiwbemservices.md) | Wskazuje, czy poświadczenia użytkownika zezwolenie na dostęp do określonej klasy IWbemServices. |
| [Funkcja BlessIWbemServicesObject](blessiwbemservicesobject.md) | Wskazuje, czy poświadczenia użytkownika zezwolenie na dostęp do określonego obiektu usługi IWbem. |
| [Funkcja Clone](clone.md) | Zwraca nowy obiekt, który jest pełny klonowania bieżącego obiektu. |
| [Funkcja CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Tworzy kopię logicznej moduł wyliczający, zachowując jego bieżącym położeniu w wyliczeniu. |
| [Funkcja CompareTo](compareto.md) | Porównuje obiekt do innego obiektu zarządzania systemu Windows. |
| [ConnectServerWmi function](connectserverwmi.md) | Tworzy połączenie przy użyciu modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze. |
| [CreateClassEnumWmi function](createclassenumwmi.md) | Zwraca moduł wyliczający dla wszystkich klas, które spełniają kryteria określonego zaznaczenia. |
| [CreateInstanceEnumWmi function](createinstanceenumwmi.md) | Zwraca moduł wyliczający, który zwraca intances określonej klasy, który spełnia kryteria wyboru określony. |
| [Funkcja Delete](delete.md) | Usuwa określonej właściwości z definicji klasy i wszystkie jego kwalifikatorów. |
| [Funkcja DeleteMethod](deletemethod.md) | Usuwa określoną metodą z definicji klasy modelu wspólnych informacji. |
| [Funkcja EndEnumeration](endenumeration.md) | Kończy sekwencji wyliczenia. | 
| [Funkcja EndMethodEnumeration](endmethodenumeration.md) | Kończy sekwencji wyliczenie uruchomiony przez wywołanie [funkcja BeginMethodEnumeration](beginmethodenumeration.md). |
| [Funkcja ExecNotificationQueryWmi](execnotificationquerywmi.md) | Wykonuje zapytanie w celu odbierania zdarzeń. |
| [Funkcja ExecQueryWmi](execquerywmi.md) | Wykonuje zapytanie w celu pobrania obiektów. |
| [Funkcja FormatFromRawValue](formatfromrawvalue.md) | Konwertuje jedną wartość danych pierwotnych wydajności w określonym formacie lub dwóch wartości danych wydajność pierwotna, jeśli Konwersja formatu jest oparte na czasie. | 
| [Funkcja Get](get.md) | Pobiera wartość określonej właściwości, jeśli istnieje. |
| [Funkcja GetCurrentApartmentType](getcurrentapartmenttype.md) | Pobiera rodzaj typu apartment, w którym jest wykonywany wywołującego. |
| [Funkcja GetDemultiplexedStub](getdemultiplexedstub.md) | Tworzy obiekt sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołania asynchroniczne z zarządzania systemu Windows. |
| [GetErrorInfo — funkcja](geterrorinfo.md) | Pobiera informacje o błędzie z poprzedniego wywołania funkcji. | 
| [Funkcja GetMethod](getmethod.md) | Pobiera informacje o określonej metody. | 
| [Funkcja GetMethodOrigin](getmethodorigin.md) | Określa klasę, w którym zadeklarowany jest metoda. |
| [Funkcja GetMethodQualifierSet](getmethodqualifierset.md) | Pobiera kwalifikator ustawić dla określonej metody. |
| [Funkcja GetNames](getnames.md) | Pobiera podzbiór lub wszystkie nazwy właściwości obiektu. |
| [Funkcja GetObjectText](getobjecttext.md) | Zwraca tekstową renderowanie obiektu składnią MOF. | 
| [Funkcja GetPropertyHandle](getpropertyhandle.md) | Zwraca unikatowy dojścia identyfikujący właściwości. |
| [Funkcja GetPropertyOrigin](getpropertyorigin.md) | Określa klasę, w którym zadeklarowany jest właściwością. |
| [Funkcja GetPropertyQualifierSet](getpropertyqualifierset.md) | Pobiera kwalifikator ustawić dla określonej właściwości.  |
| [Funkcja GetQualifierSet](getqualifierset.md) | Pobiera kwalifikator dla wystąpienia klasy lub definicji klasy. |
| [Funkcja InheritsFrom](inheritsfrom.md) | Określa, czy bieżącej klasy lub wystąpienia jest pochodną klasy określonego elementu nadrzędnego. |
| [Initialize — funkcja](initialize.md) | Wykonuje inicjowania usługi WMI. |
| [Funkcja Next](next.md) | Pobiera dalej właściwości w wyliczeniu. | 
| [Funkcja NextMethod](nextmethod.md) | Pobiera metodę dalej w wyliczeniu. |
| [Put — funkcja](put.md) | Ustawia właściwość o nazwie na nową wartość. |
| [PutClassWmi function](putclasswmi.md) | Tworzy nową klasę lub aktualizuje istniejący zestaw. |
| [PutInstanceWmi function](putinstancewmi.md) | Tworzy lub aktualizuje wystąpienia istniejącej klasy. Wystąpienie jest zapisywany w repozytorium WMI. |
| [Funkcja PutMethod](putmethod.md) | Tworzy metodę. |
| [Funkcja QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) | Resetuje moduł wyliczający kwalifikatory obiekt na początek wyliczenia. |
| [Funkcja QualifierSet_Delete](qualifierset-delete.md) | Usuwa określony kwalifikatora według nazwy.  |
| [Funkcja QualifierSet_EndEnumeration](qualifierset-endenumeration.md) | Kończy wyliczenie uruchomione za pomocą wywołania `QualifierSet_BeginEnumeration` funkcji. |
| [Funkcja QualifierSet_Get](qualifierset-get.md) | Pobiera określony nazwany kwalifikatora.  |
| [Funkcja QualifierSet_GetNames](qualifierset-getnames.md) | Pobiera nazwy wszystkich kwalifikatorów lub określony kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości. |
| [Funkcja QualifierSet_Next](qualifierset-next.md) | Pobiera kwalifikator dalej w wyliczeniu, który uruchomił się wywołaniem do [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji. |
| [Funkcja QualifierSet_Put](qualifierset-put.md) | Zapisuje kwalifikator o nazwie i wartości. |
| [Funkcja ResetSecurity](resetsecurity.md) | Przypisuje token personifikacji dostarczony do bieżącego wątku. |
| [Funkcja SetSecurity](setsecurity.md) | Pobiera token personifikacji skojarzone z bieżącego wątku. |
| [Funkcja SpawnDerivedClass](spawnderivedclass.md) | Tworzy obiekt klasy pochodnej nowo od określonego obiektu. | 
| [Funkcja SpawnInstance](spawninstance.md) | Tworzy nowe wystąpienie klasy. |   
| [Funkcja VerifyClient](verifyclientkey.md) | Zapewnia, że klucz klienta ma poprawnych zabezpieczeń. |
| [Funkcja WritePropertyValue](writepropertyvalue.md) | Zapisuje określoną liczbę bajtów do właściwości identyfikowany przez dojście właściwości. |

 ## <a name="see-also"></a>Zobacz także
[Niezarządzany wykaz interfejsów API](../index.md) 
