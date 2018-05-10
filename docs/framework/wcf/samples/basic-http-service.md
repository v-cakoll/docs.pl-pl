---
title: Podstawowa usługa HTTP
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 0f93b43a08f586e99d8a49379cfb2e283ff7918d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="basic-http-service"></a>Podstawowa usługa HTTP
W tym przykładzie pokazano, jak implementacji usługi oparte na protokole HTTP, opartego na protokole RPC - popularly określonych jako usługa "POX" (zwykły starego XML) — za pomocą modelu programowania REST Windows Communication Foundation (WCF). Ten przykład zawiera dwa składniki: samodzielnie hostowana usługa HTTP usług WCF (Service.cs) i aplikacji konsoli (Program.cs), która tworzy usługi i wykonywania wywołań do niego.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Usługi WCF udostępnia operacje 2 `EchoWithGet` i `EchoWithPost`, która zwraca ciąg, który został przekazany jako dane wejściowe.  
  
 `EchoWithGet` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebGetAttribute>, co oznacza, że operacji przetwarza HTTP `GET` żądań. Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> jawnie nie określa <xref:System.UriTemplate>, operacja oczekuje ciąg wejściowy można przesłać za pomocą parametru ciągu zapytania o nazwie `s`. Należy pamiętać, że format identyfikatora URI, który oczekuje usługi można dostosować za pomocą <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> właściwości.  
  
 `EchoWithPost` Operacji jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebInvokeAttribute>, co oznacza brak `GET` operacji (ma efekty uboczne). Ponieważ <xref:System.ServiceModel.Web.WebInvokeAttribute> jawnie nie określa `Method`, operacja przetwarza HTTP `POST` żądania, które mają ciąg w treści żądania (w formacie XML, na przykład). Należy pamiętać, że metoda HTTP i formatu identyfikatora URI dla żądania można dostosować za pomocą <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> i <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> właściwości odpowiednio.  
  
 Plik App.config Konfiguruje usługi WCF z domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> mający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ustawioną właściwość `true`. W związku z tym infrastruktura WCF tworzy automatyczne strona pomocy HTML oparte na `http://localhost:8000/Customers/help` udostępniająca informacje dotyczące konstruowania żądania HTTP do usługi i korzystać z usługi odpowiedzi HTTP.  
  
 Plik program.cs pokazano, jak fabryki kanałów WCF może służyć do wykonywania wywołań do usługi i przetwarzanie odpowiedzi. Należy pamiętać, że jest tylko jeden sposób uzyskiwania dostępu do usługi WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak <xref:System.Net.HttpWebRequest> i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takich jak [automatycznego wyboru formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) próbki i [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) przykładowe) pokazują, jak używać tych klas do komunikowania się z usługą WCF.  
  
 Próbka składa się samodzielnie hostowana usługa i klient że działać zarówno w aplikacji konsoli. Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie przykładowej podstawowa usługa Http. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator przykładowej może zostać pomyślnie uruchomiony. To zrobić, klikając prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikony, jak i wybierając **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B Skompiluj rozwiązanie, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację konsoli bez debugowania. W oknie konsoli zostanie wyświetlony i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi. W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. Jak działa próbki, klient zapisuje stan bieżącego działania.  
  
3.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyczne wybieranie formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [Podstawowa usługa obsługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md)
