---
title: Podstawowa usługa obsługi zasobów
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 2d55aecfdf6579b1de4c0cc324e59e23c251b12d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520139"
---
# <a name="basic-resource-service"></a>Podstawowa usługa obsługi zasobów
W tym przykładzie pokazano, jak zaimplementować przy użyciu modelu programowania REST Windows Communication Foundation (WCF), który udostępnia zbiorze klientów, który obsługuje pobieranie usługi oparte na protokole HTTP, dodawania, usuwania i zamienianie operacji. W tym przykładzie zawiera składniki 2 - samodzielnie hostowana usługa HTTP programu WCF (Service.cs) i aplikacji konsoli (program.cs), która tworzy usługę i wykonywania wywołań do niego.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Usługa WCF udostępnia zbiorze klientów w sposób zasobów zorientowanej na/stałej. Krótko mówiąc to niezbędnym unikatowych identyfikatorów URI dla kolekcji klientów i każdy klient korzystający z kolekcji. Usługa obsługuje wysyłanie HTTP `GET` w kolekcji identyfikatora URI, aby pobrać całą kolekcję i HTTP `POST` w kolekcji identyfikatora URI, aby dodać nowego klienta do kolekcji. Również o identyfikatorze URI dla indywidualnego klienta obsługuje HTTP `GET` Aby uzyskać szczegółowe informacje, HTTP klienta `PUT` zastąpić szczegóły klientów i HTTP `DELETE` Aby usunąć klienta z kolekcji. Po dodaniu nowego klienta do kolekcji usługi przypisuje mu unikatowy identyfikator URI i przechowuje identyfikator URI jako część szczegóły klienta. Ponadto komunikuje identyfikator URI do klienta przy użyciu nagłówka HTTP lokalizacji odpowiedzi.  
  
 Plik App.config Konfiguruje usługi WCF z domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> zawierający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> właściwością `true`. W rezultacie WCF tworzy stronę automatyczne pomocy oparty na języku HTML na `http://localhost:8000/Customers/help` zawierający informacje dotyczące sposobu tworzenia HTTP żądania do usługi oraz sposób dostępu do odpowiedzi HTTP usługi — na przykład przykładem sposobu jest szczegóły klienta reprezentowane w XML i JSON.  
  
 Udostępnianie kolekcji klientów (i bardziej ogólnie rzecz biorąc, dowolnego zasobu) w ten sposób umożliwia klientowi korzystać z niego w jednolity sposób korzystania z identyfikatorów URI i HTTP `GET`, `PUT`, `DELETE` i `POST`. Program.cs pokazuje, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest to tylko jeden sposób uzyskiwania dostępu do usługi REST programu WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak <xref:System.ServiceModel.ChannelFactory> i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takie jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatyczne wybieranie formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowy) pokazują, jak używać tych klas do komunikowania się z usługą WCF.  
  
 Przykład składa się samodzielnie hostowana usługa i klient że uruchamiane zarówno w aplikacji konsoli. Po uruchomieniu aplikacji konsolowej klienta zgłasza żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie, podstawowe przykładowej usługi zasobów. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator na potrzeby przykładu zostać pomyślnie uruchomiony. W tym celu kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierając polecenie **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację konsoli. W oknie konsoli pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. Po uruchomieniu przykładu klienta zapisuje stan bieżącego działania.  
  
3.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Automatyczne wybieranie formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
