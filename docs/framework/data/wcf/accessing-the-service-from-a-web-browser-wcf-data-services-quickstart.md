---
title: Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (WCF Data Services — Szybki Start)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: ebeda2805f3393b298e43aa4dcc601298ce176f6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330327"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (WCF Data Services — Szybki Start)

To drugie zadanie tego przewodnika Szybki Start usług danych WCF. To zadanie służy do start usług danych WCF w programie Visual Studio i opcjonalnie Wyłącz odczytu kanału informacyjnego w przeglądarce sieci Web. Możesz następnie pobierania dokumentu definicji usługi oraz dostęp do zasobów usługi danych przez przesłanie żądania HTTP GET, za pośrednictwem przeglądarki sieci Web do narażonych zasobów.

> [!NOTE]
> Domyślnie program Visual Studio automatycznie przypisuje numer portu `localhost` identyfikatora URI na tym komputerze. To zadanie używa numeru portu `12345` w przykładach identyfikatora URI. Aby uzyskać więcej informacji na temat sposobu ustawiania określonego numeru portu w projekcie programu Visual Studio zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Aby zażądać domyślnego dokumentu usługi za pomocą programu Internet Explorer

1. W programie Internet Explorer z **narzędzia** menu, wybierz opcję **Opcje internetowe**, kliknij przycisk **zawartości** kliknij pozycję **ustawienia**i wyczyść  **Włącz wyświetlanie kanału informacyjnego**.

     Dzięki temu który kanału informacyjnego odczytu jest wyłączony. Jeśli nie można wyłączyć tę funkcję, przeglądarki sieci Web będzie traktowany zwrócone zakodowanego dokumentu AtomPub jako źródła danych zamiast wyświetlanie danych pierwotnych XML pliku XML.

    > [!NOTE]
    > Jeśli przeglądarka nie może wyświetlić źródła danych jako nieprzetworzone dane XML, nadal należy możliwość wyświetlania źródła danych jako kod źródłowy dla strony.

2. W programie Visual Studio, naciśnij klawisz **F5** klawisz, aby rozpocząć debugowanie aplikacji.

3. Otwórz przeglądarkę internetową na komputerze lokalnym. Na pasku adresu wpisz następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc
    ```

     Spowoduje to zwrócenie usługi dokument domyślny, która zawiera listę zestawów encji, udostępnianych przez usługę danych.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Aby dostęp do jednostki zestaw zasobów z przeglądarki sieci Web

1. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     To zwraca zestaw wszystkich klientów w bazie danych Northwind.

2. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Spowoduje to zwrócenie wystąpienie jednostki dla określonego klienta `ALFKI`.

3. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     To jest przesyłany relacji między danymi klientów i zamówień do zwrócenia zbiór wszystkich zamówień dla konkretnego klienta `ALFKI`.

4. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     Filtruje zamówienia, które należą do określonego odbiorcy `ALFKI` tak, aby w określonej kolejności są zwracane na podstawie podane `OrderID` wartość.

## <a name="next-steps"></a>Następne kroki

Pomyślnie uzyskano dostęp usługi danych WCF, za pomocą przeglądarki sieci Web, za pomocą przeglądarki wystawiającego żądania HTTP GET do określonych zasobów. Przeglądarki sieci Web zapewnia prosty sposób do eksperymentowania przy użyciu składni adresowania żądań i wyświetlić wyniki. Jednak usługa danych produkcyjnych nie jest ogólnie dostępny przez tę metodę. Zazwyczaj aplikacje wchodzą w interakcję z usługą danych przy użyciu aplikacji kod lub języków skryptów. Następnie utworzysz aplikację kliencką, która korzysta z bibliotek klienta na dostęp do zasobów usługi danych, tak, jakby były one wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów:

> [!div class="nextstepaction"]
> [Tworzenie aplikacji klienckich programu .NET Framework](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
