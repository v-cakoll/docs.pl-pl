---
title: Podstawowa usługa obsługi zasobów
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 62b2b863f38647e81468065fd69fc4933afc5b16
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803731"
---
# <a name="basic-resource-service"></a>Podstawowa usługa obsługi zasobów
W tym przykładzie przedstawiono sposób wdrożenia oparte na protokole HTTP usługi przy użyciu modelu programowania REST Windows Communication Foundation (WCF) udostępnia kolekcję klientów obsługuje pobieranie, dodawania, usuwania i zamienianie operacji. Ten przykład zawiera składniki 2 - samodzielnie hostowana usługa HTTP usług WCF (Service.cs) i aplikacji konsoli (program.cs), która tworzy usługi i wykonywania wywołań do niego.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Usługi WCF udostępnia kolekcję klientów w sposób zasobów ukierunkowane/REST. Innymi słowy ten proces obejmuje o unikatowych identyfikatorów URI dla kolekcji klientów i wszystkich klientów w kolekcji. Usługa obsługuje wysyłanie HTTP `GET` w kolekcji identyfikator URI, aby pobrać całą kolekcję i HTTP `POST` w kolekcji identyfikator URI, aby dodać nowego klienta do kolekcji. Również na identyfikator URI dla poszczególnych klientów, obsługuje on HTTP `GET` Aby uzyskać szczegółowe informacje, HTTP klienta `PUT` zastąpić szczegóły klienta i HTTP `DELETE` Aby usunąć klienta z kolekcji. Po dodaniu nowego klienta do kolekcji, usługa przypisuje mu unikatowy identyfikator URI i przechowuje identyfikator URI jako część szczegóły klienta. Ponadto on komunikuje się identyfikator URI do klienta przy użyciu nagłówka HTTP lokalizacji odpowiedzi.  
  
 Plik App.config Konfiguruje usługi WCF z domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> mający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ustawioną właściwość `true`. W związku z tym usługi WCF tworzy stronę pomocy oparty na języku HTML automatyczne w `http://localhost:8000/Customers/help` udostępniająca informacje dotyczące sposobu tworzenia HTTP żądania do usługi oraz sposób dostępu odpowiedzi HTTP usługi — na przykład przykładem sposobu jest szczegóły klienta reprezentowane w pliku XML i JSON.  
  
 Udostępnianie kolekcji klienta (i bardziej ogólnie wszystkich zasobów) w ten sposób umożliwia klientowi interakcję z nią w jednolity sposób, przy użyciu identyfikatorów URI i HTTP `GET`, `PUT`, `DELETE` i `POST`. Program.cs pokazano, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest tylko jeden sposób uzyskać dostęp do usługi WCF REST. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak <xref:System.ServiceModel.ChannelFactory> i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takich jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatycznego wyboru formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowe) pokazują, jak używać tych klas do komunikowania się z usługą WCF.  
  
 Próbka składa się samodzielnie hostowana usługa i klient że działać zarówno w aplikacji konsoli. Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie podstawowe przykładowej usługi zasobów. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator przykładowej może zostać pomyślnie uruchomiony. To zrobić, klikając prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikony, jak i wybierając **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację konsoli. W oknie konsoli zostanie wyświetlony i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi. W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. Jak działa próbki, klient zapisuje stan bieżącego działania.  
  
3.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Automatyczne wybieranie formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
