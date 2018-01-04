---
title: AspNetRouteIntegration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf4f96116e8a4e687e7818796fa4b95e1b9b171a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
W tym przykładzie pokazano, jak udostępniać [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kieruje usługi REST przy użyciu platformy ASP.NET. [Podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) przykładowe pokazuje siebie wersję tego scenariusza i implementacji usługi szczegółowo omówiono. Ten temat koncentruje się na funkcji integracji ASP.NET. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ASP.NET routingu, zobacz <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Usługi udostępnia kolekcję klientów w sposób zasobów ukierunkowane/REST. Podobnie jak opartego na protokole SOAP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, usługi mogą być hostowane w programie ASP.NET przy użyciu pliku svc. Jednak to często nie jest preferowane w przypadku scenariuszy HTTP ponieważ wymaga ona o .svc w adresie URL dla usługi. Ponadto wymaga wdrażanie pliku svc wraz z biblioteki usługi. Ograniczenia te można uniknąć przez usługę przy użyciu tras platformy ASP.NET, jak przedstawiono w przykładach w tym przykładzie.  
  
 Przykład hostuje usługę w programie ASP.NET, dodając <xref:System.ServiceModel.Activation.ServiceRoute> w pliku Global.asax. <xref:System.ServiceModel.Activation.ServiceRoute> Określa typ usługi ("Usługa" w tym przypadku), typ fabryki hostów usług dla usługi (<xref:System.ServiceModel.Activation.WebServiceHostFactory> w takim przypadku) i HTTP podstawowy adres usługi ("~ / klientów w tym przypadku).  
  
 Oprócz tego przykładu zawiera plik Web.config, który dodaje <xref:System.Web.Routing.UrlRoutingModule> (Aby włączyć trasy ASP.NET) i obejmuje konfigurację usługi. W szczególności konfiguruje konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z domyślną <xref:System.ServiceModel.Description.WebHttpEndpoint> mający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ustawienie `true`. W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury tworzy automatyczne strona pomocy HTML oparte na `http://localhost/Customers/help` udostępniająca informacje dotyczące sposobu tworzenia HTTP żądania do usługi oraz sposób dostępu odpowiedzi HTTP usługi — na przykład przykładem Szczegóły klienta znajdują się w pliku XML i JSON.  
  
 Udostępnianie kolekcji klienta (i bardziej ogólnie wszystkich zasobów) w ten sposób umożliwia klientowi interakcję z usługą w jednolity sposób, przy użyciu identyfikatorów URI i HTTP `GET`, `PUT`, `DELETE` i `POST`.  
  
 Program.CS w projekcie klienta pokazano, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest to po prostu jednokierunkowej dostępu do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fabryki kanałów i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takich jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatycznego wyboru formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowe) pokazują, jak używać tych klas do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Zobacz też
