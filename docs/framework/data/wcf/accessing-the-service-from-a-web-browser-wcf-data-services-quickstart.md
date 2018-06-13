---
title: Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Szybki Start usługi danych WCF)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: b7fcead5eed2dd4c0c779d9a881563a39f88d094
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364008"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Uzyskiwanie dostępu do usługi z przeglądarki sieci Web (Szybki Start usługi danych WCF)
W tym zadaniu rozpocznie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z programu Visual Studio i opcjonalnie Wyłącz strumieniowe źródło odczytu w przeglądarce sieci Web. Możesz zostanie następnie pobrać dokumentu definicji usługi a także uzyskiwać dostęp do danych usługi zasobów poprzez przesłanie żądania HTTP GET za pośrednictwem przeglądarki sieci Web do narażonych zasobów.  
  
> [!NOTE]
>  Domyślnie program Visual Studio automatycznie przypisanie numeru portu do `localhost` identyfikatora URI na tym komputerze. To zadanie używa numeru portu `12345` w przykładach identyfikatora URI. Aby uzyskać więcej informacji na temat sposobu ustawiania określonego numeru portu w projekcie programu Visual Studio zobacz [Tworzenie usługi danych](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Aby zażądać domyślny dokument usługi przy użyciu programu Internet Explorer  
  
1.  W programie Internet Explorer z **narzędzia** menu, wybierz opcję **Opcje internetowe**, kliknij przycisk **zawartości** , kliknij pozycję **ustawienia**i wyczyść  **Włącz funkcję przeglądania źródła**.  
  
     Dzięki temu tego źródła odczytu jest wyłączona. Jeśli nie można wyłączyć tę funkcję, przeglądarki sieci Web będzie traktowany zwrócony AtomPub dokumentu zakodowane jako XML źródła danych zamiast nieprzetworzone dane XML.  
  
    > [!NOTE]
    >  Przeglądarka nie może wyświetlić źródła danych jako nieprzetworzone dane XML, nadal należy mogła wyświetlać źródła danych jako kod źródłowy dla strony.  
  
2.  W programie Visual Studio naciśnij klawisz F5, aby rozpocząć debugowania aplikacji.  
  
3.  Otwórz przeglądarkę sieci Web na komputerze lokalnym. Na pasku adresu wpisz następujący identyfikator URI:  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     To polecenie zwróci usługi dokument domyślny, który znajduje się lista zestawów jednostek, które są udostępniane przez tę usługę danych.  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a>Aby dostęp do jednostki zestaw zasobów z przeglądarki sieci Web  
  
1.  Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     To zwraca zestaw wszystkich klientów w bazie danych Northwind.  
  
2.  Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     To polecenie zwróci wystąpienia jednostki dla określonego klienta i `ALFKI`.  
  
3.  Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     To jest przesyłany relacji między klientami a zamówienia zwraca zestaw wszystkich zleceń dla określonego klienta `ALFKI`.  
  
4.  Na pasku adresu przeglądarki sieci Web wprowadź następujący identyfikator URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     Filtry to zlecenia, które należą do określonego klienta `ALFKI` tak, aby w dowolnej kolejności jest zwróconych na podstawie wybranych `OrderID` wartość.  
  
## <a name="next-steps"></a>Następne kroki  
 Pomyślnie uzyskano dostęp [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z przeglądarki sieci Web z wystawiania HTTP GET przeglądarką żądania do określonych zasobów. Przeglądarki sieci Web zapewnia prosty sposób na wypróbowanie składni adresowania żądań i wyświetlić wyniki. Usługi danych produkcyjnych nie jest jednak ogólnie dostępna przez tę metodę. Zazwyczaj aplikacje interakcji z usługą danych za pośrednictwem aplikacji kod lub języków skryptów. Następnie utworzysz aplikacji klienckiej, która korzysta z bibliotek klienta można uzyskać dostępu do zasobów usług danych, tak jakby były wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów:  
  
 [Tworzenie aplikacji klienckich programu .NET Framework](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
