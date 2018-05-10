---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 671857b0ace2e18f0dac7fd8033a20f3af889c8b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
W tym przykładzie pokazano, jak udostępniać usługi Windows Communication Foundation (WCF) REST przy użyciu tras platformy ASP.NET. [Podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) przykładowe pokazuje siebie wersję tego scenariusza i implementacji usługi szczegółowo omówiono. Ten temat koncentruje się na funkcji integracji ASP.NET. Aby uzyskać więcej informacji o routingu platformy ASP.NET, zobacz <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Usługi WCF udostępnia kolekcję klientów w sposób zasobów ukierunkowane/REST. Podobnie jak usługi WCF opartego na protokole SOAP usługi mogą być hostowane w programie ASP.NET przy użyciu pliku svc. Jednak to często nie jest preferowane w przypadku scenariuszy HTTP ponieważ wymaga ona o .svc w adresie URL dla usługi. Ponadto wymaga wdrażanie pliku svc wraz z biblioteki usługi. Ograniczenia te można uniknąć przez usługę przy użyciu tras platformy ASP.NET, jak przedstawiono w przykładach w tym przykładzie.  
  
 Przykład hostuje usługę w programie ASP.NET, dodając <xref:System.ServiceModel.Activation.ServiceRoute> w pliku Global.asax. <xref:System.ServiceModel.Activation.ServiceRoute> Określa typ usługi ("Usługa" w tym przypadku), typ fabryki hostów usług dla usługi (<xref:System.ServiceModel.Activation.WebServiceHostFactory> w takim przypadku) i HTTP podstawowy adres usługi ("~ / klientów w tym przypadku).  
  
 Oprócz tego przykładu zawiera plik Web.config, który dodaje <xref:System.Web.Routing.UrlRoutingModule> (Aby włączyć trasy ASP.NET) i obejmuje konfigurację usługi. W szczególności konfiguracji konfiguruje usługi WCF z domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> mający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ustawienie `true`. W związku z tym infrastruktura WCF tworzy automatyczne strona pomocy HTML oparte na `http://localhost/Customers/help` udostępniająca informacje dotyczące sposobu tworzenia HTTP żądania do usługi oraz sposób dostępu odpowiedzi HTTP usługi — na przykład przykładem klienta szczegółowe informacje znajdują się w pliku XML i JSON.  
  
 Udostępnianie kolekcji klienta (i bardziej ogólnie wszystkich zasobów) w ten sposób umożliwia klientowi interakcję z usługą w jednolity sposób, przy użyciu identyfikatorów URI i HTTP `GET`, `PUT`, `DELETE` i `POST`.  
  
 Program.CS w projekcie klienta pokazano, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest tylko jeden sposób uzyskiwania dostępu do usługi WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak fabryki kanałów WCF i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takich jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatycznego wyboru formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowe) pokazują, jak używać tych klas do komunikowania się z usługą WCF.  
  
 W tym przykładzie składa się z 3 projektów:  
  
 Usługa  
 Projekt aplikacji sieci Web, która obejmuje usługi HTTP usług WCF hostowanych w programie ASP.NET.  
  
 Klient  
 Projekt aplikacji konsoli, który nawiązuje połączeń z usługą.  
  
 Wspólne  
 Biblioteki udostępnionej, który zawiera `Customer` typ używany przez klienta i usługi. Podczas działania aplikacji konsoli klienta, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie przykładowej integracji tras platformy ASP.NET w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Jeśli go nie jest jeszcze otwarty, naciśnij klawisz "CTRL + W S" Aby otworzyć **Eksploratora rozwiązań** okna.  
  
4.  Z **Eksploratora rozwiązań** systemu windows, kliknij prawym przyciskiem myszy **usługi** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **Start Nowe wystąpienie** menu kontekstowe pojawia się i wybierz **uruchomić nowe wystąpienie**.  Spowoduje to uruchomienie ASP.NET development server, który obsługuje usługę.  
  
5.  Z **Eksploratora rozwiązań** systemu windows, kliknij prawym przyciskiem myszy **klienta** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowy Wystąpienie** menu kontekstowe pojawia się i wybierz **uruchomić nowe wystąpienie**.  
  
6.  Okno konsoli klienta pojawia się i zawiera identyfikator URI uruchomionej usługi i identyfikator URI elementu HTML pomocy strony uruchomionej usługi. W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. Jak działa próbki, klient zapisuje stan bieżącego działania.  
  
7.  Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji konsoli klienta.  
  
8.  Naciśnij klawisz Shift + F5, aby zatrzymać debugowanie usługi, w obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę ASP.NET development serwera i wybierz **zatrzymać** z menu kontekstowego.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Zobacz też
