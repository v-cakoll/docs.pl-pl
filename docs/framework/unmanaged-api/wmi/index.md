---
title: Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)
description: Podsumowuje niezarządzany interfejs API programu .NET Framework dla informacji o wyrobach WMI i liczniku wydajności.
ms.date: 11/06/2017
ms.openlocfilehash: f28cd25ee6c3511dc5ac8a6dd4076c81f43fe74a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127417"
---
# <a name="windows-management-instrumentation-wmi-and-performance-counters-unmanaged-api-reference"></a>Instrumentacja zarządzania windowsem (WMI) i liczniki wydajności (odwołanie do niezarządzanego interfejsu API)

Niezarządzany interfejs API w programie .NET Framework WMI i liczniki wydajności składa się z zestawu funkcji, które zawijania wywołań do [natywnego interfejsu API instrumentacji zarządzania windows](/windows/desktop/WmiSdk/com-api-for-wmi). Umożliwia tworzenie narzędzi i bibliotek, które zarządzają zdalnymi systemami komputerowymi i monitorują go.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

Interfejs API zawiera następujące funkcje:

| Funkcja | Opis |
|---------|---------|
| [Funkcja BeingEnumeration](beginenumeration.md) | Resetuje wyliczacz do początku wyliczenia właściwości obiektu WMI. |
| [Funkcja BeginMethodEnumeration](beginmethodenumeration.md) |  Rozpoczyna wyliczenie metod dostępnych dla obiektu. |
| [Funkcja BlessIWbemServices](blessiwbemservices.md) | Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonej klasy IWbemServices. |
| [Funkcja BlessIWbemServicesObject](blessiwbemservicesobject.md) | Wskazuje, czy poświadczenia użytkownika zezwalają na dostęp do określonego obiektu usługi IWbem. |
| [Funkcja Clone](clone.md) | Zwraca nowy obiekt, który jest kompletnym klonem bieżącego obiektu. |
| [Funkcja CloneEnumWbemClassObject](cloneenumwbemclassobject.md) | Tworzy logiczną kopię modułu wyliczającego, zachowując jego bieżącą pozycję w wyliczeniu. |
| [Funkcja CompareTo](compareto.md) | Porównuje obiekt z innym obiektem zarządzania systemem Windows. |
| [ConnectServerWmi, funkcja](connectserverwmi.md) | Tworzy połączenie za pośrednictwem dcom do obszaru nazw WMI na określonym komputerze. |
| [CreateClassEnumWmi, funkcja](createclassenumwmi.md) | Zwraca wyliczenie dla wszystkich klas, które spełniają określone kryteria wyboru. |
| [CreateInstanceEnumWmi, funkcja](createinstanceenumwmi.md) | Zwraca wyliczyć, który zwraca wystąpienia określonej klasy, które spełniają określone kryteria wyboru. |
| [Funkcja Delete](delete.md) | Usuwa określoną właściwość z definicji klasy i wszystkich jej kwalifikatorów. |
| [Funkcja DeleteMethod](deletemethod.md) | Usuwa określoną metodę z definicji klasy CIM. |
| [Funkcja EndEnumeration](endenumeration.md) | Kończy sekwencję wyliczenia. |
| [Funkcja EndMethodEnumeration](endmethodenumeration.md) | Kończy sekwencję wyliczenia rozpoczętą przez wywołanie [funkcji BeginMethodEnumeration](beginmethodenumeration.md). |
| [ExecNotificationQueryWmi, funkcja](execnotificationquerywmi.md) | Wykonuje kwerendę do odbierania zdarzeń. |
| [Funkcja ExecQueryWmi](execquerywmi.md) | Wykonuje kwerendę w celu pobrania obiektów. |
| [FormatFromRawValue, funkcja](formatfromrawvalue.md) | Konwertuje jedną wartość danych wydajności pierwotnej na określony format lub dwie wartości danych wydajności pierwotnej, jeśli konwersja formatu jest oparta na czasie. |
| [Get, funkcja](get.md) | Pobiera określoną wartość właściwości, jeśli istnieje. |
| [GetCurrentApartmentType, funkcja](getcurrentapartmenttype.md) | Pobiera typ mieszkania, w którym wywoływany jest. |
| [GetDemultiplexedStub, funkcja](getdemultiplexedstub.md) | Tworzy ujście usługi przesyłania dalej obiektu, aby pomóc klientowi w odbieraniu wywołań asynchronicznych z zarządzania systemem Windows. |
| [GetErrorInfo, funkcja](geterrorinfo.md) | Pobiera informacje o błędzie z poprzedniego wywołania funkcji. |
| [GetMethod, funkcja](getmethod.md) | Pobiera informacje o określonej metodzie. |
| [GetMethodOrigin, funkcja](getmethodorigin.md) | Określa klasę, w której metoda jest zadeklarowana. |
| [GetMethodQualifierSet, funkcja](getmethodqualifierset.md) | Pobiera zestaw kwalifikator dla określonej metody. |
| [GetNames, funkcja](getnames.md) | Pobiera podzbiór lub wszystkie nazwy właściwości obiektu. |
| [GetObjectText, funkcja](getobjecttext.md) | Zwraca teksturowane renderowanie obiektu w składni MOF. |
| [GetPropertyHandle, funkcja](getpropertyhandle.md) | Zwraca unikatowy dojście, który identyfikuje właściwość. |
| [GetPropertyOrigin, funkcja](getpropertyorigin.md) | Określa klasę, w której jest zadeklarowana właściwość. |
| [GetPropertyQualifierSet, funkcja](getpropertyqualifierset.md) | Pobiera zestaw kwalifikator dla określonej właściwości.  |
| [GetQualifierSet, funkcja](getqualifierset.md) | Pobiera zestaw kwalifikator dla wystąpienia klasy lub definicji klasy. |
| [InheritsFrom, funkcja](inheritsfrom.md) | Określa, czy bieżąca klasa lub wystąpienie pochodzi od określonej klasy nadrzędnej. |
| [Inicjowanie funkcji](initialize.md) | Wykonuje inicjowanie WMI. |
| [Następna funkcja](next.md) | Pobiera następną właściwość w wyliczeniu. |
| [NextMetoda, funkcja](nextmethod.md) | Pobiera następną metodę w wyliczeniu. |
| [Umieść, funkcja](put.md) | Ustawia nazwaną właściwość na nową wartość. |
| [PutClassWmi, funkcja](putclasswmi.md) | Tworzy nową klasę lub aktualizuje istniejącą. |
| [PutInstanceWmi, funkcja](putinstancewmi.md) | Tworzy lub aktualizuje wystąpienie istniejącej klasy. Wystąpienie jest zapisywane w repozytorium WMI. |
| [PutMethod, funkcja](putmethod.md) | Tworzy metodę. |
| [QualifierSet_BeginEnumeration funkcja](qualifierset-beginenumeration.md) | Resetuje wyliczenia kwalifikatora obiektu na początku wyliczenia. |
| [QualifierSet_Delete funkcja](qualifierset-delete.md) | Usuwa określony kwalifikator według nazwy.  |
| [QualifierSet_EndEnumeration funkcja](qualifierset-endenumeration.md) | Kończy wyliczenie rozpoczęte wywołaniem `QualifierSet_BeginEnumeration` funkcji. |
| [QualifierSet_Get funkcja](qualifierset-get.md) | Pobiera określony nazwany kwalifikator.  |
| [QualifierSet_GetNames funkcja](qualifierset-getnames.md) | Pobiera nazwy wszystkich kwalifikatorów lub określonych kwalifikatorów, które są dostępne z bieżącego obiektu lub właściwości. |
| [QualifierSet_Next funkcja](qualifierset-next.md) | Pobiera następny kwalifikator w wyliczeniu, który rozpoczął się od wywołania funkcji [QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md) |
| [QualifierSet_Put funkcja](qualifierset-put.md) | Zapisuje nazwany kwalifikator i wartość. |
| [ResetSecurity, funkcja](resetsecurity.md) | Przypisuje dostarczony token personifikacji do bieżącego wątku. |
| [SetSecurity, funkcja](setsecurity.md) | Pobiera token personifikacji skojarzony z bieżącym wątkiem. |
| [SpawnDerivedClass, funkcja](spawnderivedclass.md) | Tworzy nowo pochodny obiekt klasy z określonego obiektu. |
| [SpawnInstance, funkcja](spawninstance.md) | Tworzy nowe wystąpienie klasy. |
| [VerifyClient, funkcja](verifyclientkey.md) | Zapewnia, że klucz klienta ma odpowiednie zabezpieczenia. |
| [WritePropertyValue, funkcja](writepropertyvalue.md) | Zapisuje określoną liczbę bajtów do właściwości identyfikowanej przez dojście do właściwości. |

## <a name="see-also"></a>Zobacz też

- [Odwołanie do interfejsu API niezarządzanego](../index.md)
