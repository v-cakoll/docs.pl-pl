---
title: Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Usługi danych programu WCF Szybki Start)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780545"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Usługi danych programu WCF Szybki Start)

Jest to drugie zadanie przewodnika Szybki Start dotyczącego Usługi danych programu WCF. W tym zadaniu można uruchomić Usługi danych programu WCF z programu Visual Studio i opcjonalnie wyłączyć odczytywanie kanału informacyjnego w przeglądarce internetowej. Następnie można pobrać dokument definicji usługi oraz uzyskać dostęp do zasobów usługi danych przez przesłanie żądań HTTP GET za pośrednictwem przeglądarki sieci Web do narażonych zasobów.

> [!NOTE]
> Domyślnie program Visual Studio przypisuje numer portu do `localhost` identyfikatora URI na komputerze. To zadanie używa numeru `12345` portu w przykładach identyfikatora URI. Aby uzyskać więcej informacji na temat sposobu ustawiania określonego numeru portu w projekcie programu Visual Studio, zobacz [Tworzenie usługi danych](creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Aby zażądać domyślnego dokumentu usługi przy użyciu programu Internet Explorer

1. W programie Internet Explorer z menu **Narzędzia** wybierz pozycję **Opcje internetowe**, kliknij kartę **zawartość** , kliknij pozycję **Ustawienia**, a następnie wyczyść pole wyboru **Włącz wyświetlanie źródła**.

     Gwarantuje to, że odczytywanie źródła danych jest wyłączone. Jeśli ta funkcja nie zostanie wyłączona, przeglądarka sieci Web będzie traktować zwracany dokument zakodowany AtomPub jako źródło danych XML zamiast wyświetlać pierwotne dane XML.

    > [!NOTE]
    > Jeśli przeglądarka nie może wyświetlić kanału informacyjnego jako pierwotne dane XML, nadal będzie można wyświetlić źródło danych jako kod źródłowy strony.

2. W programie Visual Studio naciśnij klawisz **F5** , aby rozpocząć debugowanie aplikacji.

3. Otwórz przeglądarkę sieci Web na komputerze lokalnym. Na pasku adresu wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc
    ```

     Spowoduje to zwrócenie domyślnego dokumentu usługi zawierającego listę zestawów jednostek, które są udostępniane przez tę usługę danych.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Aby uzyskać dostęp do zasobów zestawu jednostek z przeglądarki sieci Web

1. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     Spowoduje to zwrócenie zestawu wszystkich klientów z przykładowej bazy danych Northwind.

2. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Spowoduje to zwrócenie wystąpienia jednostki dla określonego klienta `ALFKI`.

3. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     Powoduje to przechodzenie między klientami i zamówieniami w celu zwrócenia zestawu wszystkich zamówień dla określonego klienta `ALFKI`.

4. Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     To filtruje zamówienia należące do określonego klienta `ALFKI` , aby tylko określona kolejność była zwracana na podstawie podanej `OrderID` wartości.

## <a name="next-steps"></a>Następne kroki

Pomyślnie uzyskano dostęp do Usługi danych programu WCF z przeglądarki sieci Web przy użyciu przeglądarki wysyłającej żądania HTTP GET do określonych zasobów. Przeglądarka sieci Web zapewnia łatwy sposób eksperymentowania z składnią adresów żądań i wyświetlania wyników. Jednak usługa danych produkcyjnych nie jest ogólnie używana przez tę metodę. Zazwyczaj aplikacje współpracują z usługą danych za pomocą kodu aplikacji lub języków skryptów. Następnie utworzysz aplikację kliencką, która używa bibliotek klienckich do uzyskiwania dostępu do zasobów usługi danych, tak jakby były obiektami środowiska uruchomieniowego języka wspólnego (CLR):

> [!div class="nextstepaction"]
> [Tworzenie aplikacji klienckich programu .NET Framework](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do zasobów usługi danych](accessing-data-service-resources-wcf-data-services.md)
