---
title: Podstawowa usługa HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: f97fcab1200b9c13860ab8030378b5402b087d7a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028266"
---
# <a name="basic-http-service"></a>Podstawowa usługa HTTP
Ten przykład demonstruje sposób implementacji usługi oparte na protokole HTTP, opartego na protokole RPC — co jest często określany jako usługa "POX" (zwykłe stare XML) — przy użyciu modelu programowania REST Windows Communication Foundation (WCF). Ten przykład zawiera dwa składniki: samodzielnie hostowana usługa HTTP programu WCF (Service.cs) i aplikacji konsoli (Program.cs), która tworzy usługę i wykonywania wywołań do niego.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Usługa WCF udostępnia operacje 2 `EchoWithGet` i `EchoWithPost`, która zwraca ciąg, który został przekazany jako dane wejściowe.  
  
 `EchoWithGet` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebGetAttribute>, co oznacza, że operacja przetwarza HTTP `GET` żądań. Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> bez określenia <xref:System.UriTemplate>, operacja oczekuje, że ciąg wejściowy przekazać za pomocą parametru ciągu zapytania o nazwie `s`. Należy pamiętać, że format identyfikatora URI, który oczekuje, że usługi można dostosować przy użyciu <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> właściwości.  
  
 `EchoWithPost` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebInvokeAttribute>, co oznacza brak `GET` operacji (ma efekty uboczne). Ponieważ <xref:System.ServiceModel.Web.WebInvokeAttribute> bez określenia `Method`, operacja przetwarza HTTP `POST` żądania, które mają ten ciąg w treści żądania (w formacie XML, na przykład). Należy pamiętać, że metoda HTTP i format identyfikatora URI żądania można dostosować za pomocą <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> i <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> właściwości odpowiednio.  
  
 Plik App.config Konfiguruje usługi WCF z domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> zawierający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> właściwością `true`. W rezultacie, infrastruktura WCF tworzy automatycznego na podstawie kodu HTML na stronie pomocy `http://localhost:8000/Customers/help` zawierające informacje dotyczące sposobu konstruowania żądania HTTP do usługi i sposobu korzystania z usługi odpowiedzi HTTP.  
  
 Plik program.cs pokazuje, jak fabryka kanałów WCF może służyć do wykonywania wywołań do usługi i przetwarzanie odpowiedzi. Należy pamiętać, że jest to tylko jeden sposób uzyskiwania dostępu do usługi WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak <xref:System.Net.HttpWebRequest> i <xref:System.Net.WebClient>.
  
 Przykład składa się samodzielnie hostowana usługa i klient że uruchamiane zarówno w aplikacji konsoli. Po uruchomieniu aplikacji konsolowej klienta zgłasza żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie, podstawowe przykładowej usługi Http. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator na potrzeby przykładu zostać pomyślnie uruchomiony. W tym celu kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierając polecenie **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację konsoli bez debugowania. W oknie konsoli pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. Po uruchomieniu przykładu klienta zapisuje stan bieżącego działania.  
  
3.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  