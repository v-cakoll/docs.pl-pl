---
title: Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)
description: Zawiera podsumowanie programu .NET Framework niezarządzanych interfejsów API dla usługi WMI i wydajności informacje licznika.
author: rpetrusha
ms.author: ronpet
ms.date: 11/06/2017
ms.openlocfilehash: 6e105bc28b6011c3177216aba996eb85c0766ac8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069514"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Instrumentacja zarządzania Windows (WMI) oraz z liczników wydajności (niezarządzany wykaz interfejsów API)

Niezarządzany API .NET Framework WMI i liczniki wydajności zawiera zestaw funkcji, które owijają odwołania do [natywnych interfejsów API usługi Instrumentacja zarządzania Windows](/windows/desktop/WmiSdk/com-api-for-wmi). Umożliwia tworzenie narzędzi i bibliotek, które zarządzanie i monitorowanie komputerów zdalnych.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
Ten interfejs API obejmuje następujące funkcje:

| Funkcja | Opis |
|---------|---------|
| [Funkcja BeingEnumeration](beginenumeration.md) | Resetuje modułu wyliczającego do stanu sprzed wyliczenie właściwości obiektu WMI. |
| [Funkcja BeginMethodEnumeration](beginmethodenumeration.md) |  Rozpoczyna się wyliczenie metody dostępne dla obiektu. |
| [Funkcja BlessIWbemServices](blessiwbemservices.md) | Wskazuje, czy poświadczenia użytkownika zezwolić na dostęp do określonej klasy IWbemServices. |
| [Funkcja BlessIWbemServicesObject](blessiwbemservicesobject.md) | Wskazuje, czy poświadczenia użytkownika zezwolić na dostęp do określonego obiektu usługi IWbem. |
| [Funkcja Clone](clone.md) | Zwraca nowy obiekt, który jest kompletny klonowania bieżącego obiektu. |
| [Funkcja CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Tworzy kopię logiczne moduł wyliczający, zachowując jego bieżącej pozycji w wyliczeniu. |
| [Funkcja CompareTo](compareto.md) | Porównuje obiekt do innego obiektu zarządzania Windows. |
| [ConnectServerWmi function](connectserverwmi.md) | Tworzy połączenie za pomocą modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze. |
| [CreateClassEnumWmi function](createclassenumwmi.md) | Zwraca moduł wyliczający dla wszystkich klas, które spełniają kryteria określonego zaznaczenia. |
| [CreateInstanceEnumWmi function](createinstanceenumwmi.md) | Zwraca moduł wyliczający, który zwraca wystąpienia określonej klasy, spełniają kryteria określonego zaznaczenia. |
| [Funkcja Delete](delete.md) | Usuwa określoną właściwość z definicji klasy i wszystkie jego kwalifikatorów. |
| [Funkcja DeleteMethod](deletemethod.md) | Usuwa określoną metodę z definicji klasy modelu wspólnych informacji. |
| [Funkcja EndEnumeration](endenumeration.md) | Kończy sekwencji wyliczenia. | 
| [Funkcja EndMethodEnumeration](endmethodenumeration.md) | Kończy sekwencji wyliczenie uruchomione przez wywołanie [funkcja BeginMethodEnumeration](beginmethodenumeration.md). |
| [Funkcja ExecNotificationQueryWmi](execnotificationquerywmi.md) | Wykonuje zapytanie, aby odbierać zdarzenia. |
| [Funkcja ExecQueryWmi](execquerywmi.md) | Wykonuje zapytanie, aby pobrać obiekty. |
| [Funkcja FormatFromRawValue](formatfromrawvalue.md) | Konwertuje jedną wartość danych pierwotnych wydajności w określonym formacie lub dwóch wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparte na czasie. | 
| [Funkcja Get](get.md) | Pobiera wartość określonej właściwości, jeśli taki istnieje. |
| [GetCurrentApartmentType — funkcja](getcurrentapartmenttype.md) | Pobiera rodzaj typu apartment, w którym jest wykonywany obiekt wywołujący. |
| [GetDemultiplexedStub — funkcja](getdemultiplexedstub.md) | Tworzy obiektu sink usługi przesyłania dalej ułatwiających klienta odbieranie wywołań asynchronicznych z zarządzania Windows. |
| [Geterrorinfo — funkcja](geterrorinfo.md) | Pobiera informacje o błędzie z poprzedniego wywołania funkcji. | 
| [Funkcja GetMethod](getmethod.md) | Pobiera informacje o określonej metody. | 
| [Funkcja GetMethodOrigin](getmethodorigin.md) | Określa klasę, w którym zadeklarowany jest metodą. |
| [Funkcja GetMethodQualifierSet](getmethodqualifierset.md) | Pobiera kwalifikator ustawione dla konkretnych metod. |
| [Funkcja GetNames](getnames.md) | Pobiera podzbiór lub wszystkie nazwy właściwości obiektu. |
| [Funkcja GetObjectText](getobjecttext.md) | Zwraca tekstową renderowanie obiektu składnią MOF. | 
| [Funkcja GetPropertyHandle](getpropertyhandle.md) | Zwraca unikatowy uchwytu, który identyfikuje właściwość. |
| [Funkcja GetPropertyOrigin](getpropertyorigin.md) | Określa klasę, w którym zadeklarowany jest właściwością. |
| [GetPropertyQualifierSet — funkcja](getpropertyqualifierset.md) | Pobiera kwalifikator, ustaw dla określonej właściwości.  |
| [GetQualifierSet — funkcja](getqualifierset.md) | Pobiera kwalifikator ustawione dla wystąpienia klasy lub definicji klasy. |
| [InheritsFrom — funkcja](inheritsfrom.md) | Określa, czy bieżącą klasę lub wystąpienie dziedziczy po określonej klasie nadrzędnej. |
| [Initialize — funkcja](initialize.md) | Wykonuje inicjowania usługi WMI. |
| [Użycie funkcji Next](next.md) | Pobiera następną właściwość w wyliczeniu. | 
| [NextMethod — funkcja](nextmethod.md) | Pobiera Następna metoda w wyliczeniu. |
| [Umieść — funkcja](put.md) | Ustawia właściwość o nazwie na nową wartość. |
| [PutClassWmi — funkcja](putclasswmi.md) | Tworzy nową klasę lub aktualizuje istniejący zestaw. |
| [PutInstanceWmi — funkcja](putinstancewmi.md) | Tworzy lub aktualizuje wystąpienia istniejącej klasy. Wystąpienie jest zapisywany do repozytorium WMI. |
| [PutMethod — funkcja](putmethod.md) | Tworzy metodę. |
| [QualifierSet_BeginEnumeration — funkcja](qualifierset-beginenumeration.md) | Resetuje moduł wyliczający kwalifikatory obiektu na początku tego wyliczenia. |
| [QualifierSet_Delete — funkcja](qualifierset-delete.md) | Usuwa określony kwalifikator według nazwy.  |
| [QualifierSet_EndEnumeration — funkcja](qualifierset-endenumeration.md) | Kończy wyliczenie uruchomione z wywołaniem `QualifierSet_BeginEnumeration` funkcji. |
| [QualifierSet_Get — funkcja](qualifierset-get.md) | Pobiera określonego nazwanego kwalifikator.  |
| [QualifierSet_GetNames — funkcja](qualifierset-getnames.md) | Pobiera nazwy wszystkich kwalifikatorów lub określony kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości. |
| [QualifierSet_Next — funkcja](qualifierset-next.md) | Pobiera następny kwalifikatora w wyliczeniu, który uruchamiany przy użyciu wywołania do [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji. |
| [QualifierSet_Put — funkcja](qualifierset-put.md) | Zapisuje kwalifikator o nazwie i wartości. |
| [ResetSecurity — funkcja](resetsecurity.md) | Przypisuje token personifikacji dostarczony do bieżącego wątku. |
| [SetSecurity — funkcja](setsecurity.md) | Pobiera token personifikacji skojarzone z bieżącym wątkiem. |
| [SpawnDerivedClass — funkcja](spawnderivedclass.md) | Tworzy obiekt klasy pochodnej nowo od określonego obiektu. | 
| [SpawnInstance — funkcja](spawninstance.md) | Tworzy nowe wystąpienie klasy. |   
| [VerifyClient — funkcja](verifyclientkey.md) | Zapewnia, że klucz klienta ma poprawne zabezpieczeń. |
| [WritePropertyValue — funkcja](writepropertyvalue.md) | Zapisuje określoną liczbę bajtów z właściwością identyfikowane przez dojście właściwości. |

 ## <a name="see-also"></a>Zobacz także
[Niezarządzany wykaz interfejsów API](../index.md) 
