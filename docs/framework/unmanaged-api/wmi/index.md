---
title: WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)
description: Podsumowuje .NET Framework niezarządzany interfejs API dla usługi WMI i informacje o liczniku wydajności.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127417"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Instrumentacja zarządzania Windows (WMI) i liczniki wydajności (niezarządzana dokumentacja interfejsu API)

Niezarządzany interfejs API usługi .NET Framework WMI i liczników wydajności składa się z zestawu funkcji, które zawijają wywołania [natywnego interfejsu api Instrumentacja zarządzania Windows](/windows/desktop/WmiSdk/com-api-for-wmi). Umożliwia tworzenie narzędzi i bibliotek, które zarządzają i monitorują zdalne systemy komputerów.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

Interfejs API zawiera następujące funkcje:

| Funkcja | Opis |
|---------|---------|
| [Funkcja BeingEnumeration](beginenumeration.md) | Resetuje moduł wyliczający na początku wyliczenia właściwości obiektu WMI. |
| [Funkcja BeginMethodEnumeration](beginmethodenumeration.md) |  Rozpoczyna Wyliczenie metod dostępnych dla obiektu. |
| [Funkcja BlessIWbemServices](blessiwbemservices.md) | Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonej klasy IWbemServices. |
| [Funkcja BlessIWbemServicesObject](blessiwbemservicesobject.md) | Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonego obiektu usługi IWbem. |
| [Funkcja Clone](clone.md) | Zwraca nowy obiekt, który jest kompletnym klonem bieżącego obiektu. |
| [Funkcja CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Tworzy logiczną kopię modułu wyliczającego, zachowując jego bieżącą pozycję w wyliczeniu. |
| [Funkcja CompareTo](compareto.md) | Porównuje obiekt z innym obiektem zarządzania systemem Windows. |
| [ConnectServerWmi, funkcja](connectserverwmi.md) | Tworzy połączenie za pomocą modelu DCOM do przestrzeni nazw usługi WMI na określonym komputerze. |
| [CreateClassEnumWmi, funkcja](createclassenumwmi.md) | Zwraca moduł wyliczający dla wszystkich klas, które spełniają określone kryteria wyboru. |
| [CreateInstanceEnumWmi, funkcja](createinstanceenumwmi.md) | Zwraca moduł wyliczający, który zwraca wystąpienia określonej klasy, które spełniają określone kryteria wyboru. |
| [Funkcja Delete](delete.md) | Usuwa określoną właściwość z definicji klasy i wszystkich jej kwalifikatorów. |
| [Funkcja DeleteMethod](deletemethod.md) | Usuwa określoną metodę z definicji klasy CIM. |
| [Funkcja EndEnumeration](endenumeration.md) | Kończy sekwencję wyliczenia. |
| [Funkcja EndMethodEnumeration](endmethodenumeration.md) | Kończy sekwencję wyliczenia rozpoczętą przez wywołanie [funkcji BeginMethodEnumeration](beginmethodenumeration.md). |
| [Funkcja ExecNotificationQueryWmi](execnotificationquerywmi.md) | Wykonuje zapytanie do odbierania zdarzeń. |
| [Funkcja ExecQueryWmi](execquerywmi.md) | Wykonuje zapytanie w celu pobrania obiektów. |
| [Funkcja FormatFromRawValue](formatfromrawvalue.md) | Konwertuje jedną pierwotną wartość danych wydajności do określonego formatu lub dwie wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparta na czasie. |
| [Funkcja Get](get.md) | Pobiera określoną wartość właściwości, jeśli istnieje. |
| [GetCurrentApartmentType, funkcja](getcurrentapartmenttype.md) | Pobiera typ apartamentu, w którym wykonywany jest obiekt wywołujący. |
| [GetDemultiplexedStub, funkcja](getdemultiplexedstub.md) | Tworzy obiekt sink usługi przesyłania dalej obiektów, który pomaga klientowi odbierać asynchroniczne wywołania z usługi Windows Management. |
| [GetErrorInfo — funkcja](geterrorinfo.md) | Pobiera informacje o błędzie z poprzedniego wywołania funkcji. |
| [Funkcja GetMethod](getmethod.md) | Pobiera informacje o określonej metodzie. |
| [Funkcja GetMethodOrigin](getmethodorigin.md) | Określa klasę, w której jest zadeklarowana Metoda. |
| [Funkcja GetMethodQualifierSet](getmethodqualifierset.md) | Pobiera kwalifikator zestawu dla określonej metody. |
| [Funkcja GetNames](getnames.md) | Pobiera podzestaw lub wszystkie nazwy właściwości obiektu. |
| [Funkcja GetObjectText](getobjecttext.md) | Zwraca renderowanie tekstu obiektu w składni MOF. |
| [Funkcja GetPropertyHandle](getpropertyhandle.md) | Zwraca unikatowy uchwyt identyfikujący właściwość. |
| [Funkcja GetPropertyOrigin](getpropertyorigin.md) | Określa klasę, w której jest zadeklarowana właściwość. |
| [GetPropertyQualifierSet, funkcja](getpropertyqualifierset.md) | Pobiera kwalifikator zestawu dla określonej właściwości.  |
| [GetQualifierSet, funkcja](getqualifierset.md) | Pobiera kwalifikator zestawu dla wystąpienia klasy lub definicji klasy. |
| [InheritsFrom, funkcja](inheritsfrom.md) | Określa, czy bieżąca Klasa lub wystąpienie pochodzi z określonej klasy nadrzędnej. |
| [Initialize — funkcja](initialize.md) | Wykonuje inicjalizację WMI. |
| [Next — funkcja](next.md) | Pobiera następną właściwość w wyliczeniu. |
| [NextMethod, funkcja](nextmethod.md) | Pobiera następną metodę w wyliczeniu. |
| [Put — funkcja](put.md) | Ustawia nazwę właściwości nazwanej na nową wartość. |
| [PutClassWmi, funkcja](putclasswmi.md) | Tworzy nową klasę lub aktualizuje istniejącą. |
| [PutInstanceWmi, funkcja](putinstancewmi.md) | Tworzy lub aktualizuje wystąpienie istniejącej klasy. Wystąpienie jest zapisywane w repozytorium WMI. |
| [PutMethod, funkcja](putmethod.md) | Tworzy metodę. |
| [QualifierSet_BeginEnumeration, funkcja](qualifierset-beginenumeration.md) | Resetuje moduł wyliczający kwalifikatorów obiektu na początku wyliczenia. |
| [QualifierSet_Delete, funkcja](qualifierset-delete.md) | Usuwa określony kwalifikator według nazwy.  |
| [QualifierSet_EndEnumeration, funkcja](qualifierset-endenumeration.md) | Kończy Wyliczenie rozpoczęte z wywołaniem funkcji `QualifierSet_BeginEnumeration`. |
| [QualifierSet_Get, funkcja](qualifierset-get.md) | Pobiera określony kwalifikator nazwany.  |
| [QualifierSet_GetNames, funkcja](qualifierset-getnames.md) | Pobiera nazwy wszystkich kwalifikatorów lub określonych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości. |
| [QualifierSet_Next, funkcja](qualifierset-next.md) | Pobiera następny kwalifikator w wyliczeniu, który rozpoczął wywołanie funkcji [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) . |
| [QualifierSet_Put, funkcja](qualifierset-put.md) | Zapisuje nazwany kwalifikator i wartość. |
| [ResetSecurity, funkcja](resetsecurity.md) | Przypisuje podany token personifikacji do bieżącego wątku. |
| [Funkcja setsecurity](setsecurity.md) | Pobiera token personifikacji skojarzony z bieżącym wątkiem. |
| [SpawnDerivedClass, funkcja](spawnderivedclass.md) | Tworzy nowo pochodny obiekt klasy na podstawie określonego obiektu. |
| [SpawnInstance, funkcja](spawninstance.md) | Tworzy nowe wystąpienie klasy. |
| [VerifyClient, funkcja](verifyclientkey.md) | Zapewnia, że klucz klienta ma poprawne zabezpieczenia. |
| [WritePropertyValue, funkcja](writepropertyvalue.md) | Zapisuje określoną liczbę bajtów do właściwości identyfikowanej przez uchwyt właściwości. |

## <a name="see-also"></a>Zobacz także

- [Niezarządzana dokumentacja interfejsu API](../index.md)
