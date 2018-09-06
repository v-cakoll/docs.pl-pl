---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 8d9a0710e5106cbc3d02a06e81f4f8ed9ae3e03b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788814"
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Niniejszy przykład pokazuje, jak hostować usługi Windows Communication Foundation (WCF) REST przy użyciu trasy ASP.NET. [Podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) przykładowy przedstawia Self-Hosted wersję tego scenariusza i implementacji usługi szczegółowo omawia. Ten temat koncentruje się na temat funkcji integracji programu ASP.NET. Aby uzyskać więcej informacji na temat routingu platformy ASP.NET, zobacz <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Usługa WCF udostępnia zbiorze klientów w sposób zasobów zorientowanej na/stałej. Podobnie jak usługi WCF opartego na protokole SOAP usługa może być hostowana na platformie ASP.NET przy użyciu pliku .svc. Jednak to często nie jest preferowane w przypadku scenariuszy HTTP ponieważ wymaga mających .svc w adresie URL usługi. Ponadto wymaga wdrażania plików .svc, wraz z biblioteki usługi. Ograniczenia te można uniknąć, udostępniając usługi przy użyciu trasy ASP.NET, jak przedstawiono w przykładach w tym przykładzie.  
  
 Przykład hostuje usługę w programie ASP.NET przez dodanie <xref:System.ServiceModel.Activation.ServiceRoute> w pliku Global.asax. <xref:System.ServiceModel.Activation.ServiceRoute> Określa typ usługi ("Usługa" w tym przypadku), typ fabryki hostów usług na potrzeby usługi (<xref:System.ServiceModel.Activation.WebServiceHostFactory> w tym przypadku) i HTTP, podstawowy adres usługi ("~ / klientów w tym przypadku).  
  
 Oprócz tego przykładu zawiera plik Web.config, który dodaje <xref:System.Web.Routing.UrlRoutingModule> (Aby włączyć trasy ASP.NET) i obejmuje konfigurację dla usługi. W szczególności konfiguracji konfiguruje usługę WCF przy użyciu domyślnego <xref:System.ServiceModel.Description.WebHttpEndpoint> zawierający <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ustawienie `true`. W rezultacie, infrastruktura WCF tworzy automatycznego na podstawie kodu HTML na stronie pomocy `http://localhost/Customers/help` zawierający informacje dotyczące sposobu tworzenia HTTP żądania do usługi i jak uzyskać dostęp odpowiedź HTTP usługi — na przykład do przykładem klienta szczegółowe informacje są przedstawione w XML i JSON.  
  
 Udostępnianie kolekcji klientów (i bardziej ogólnie rzecz biorąc, dowolnego zasobu) w ten sposób umożliwia klientowi do interakcji z usługą w jednolity sposób korzystania z identyfikatorów URI i HTTP `GET`, `PUT`, `DELETE` i `POST`.  
  
 Plik program.CS w projekcie klienta pokazuje, jak takiego klienta mogą być tworzone za pomocą <xref:System.Net.HttpWebRequest>. Należy pamiętać, że jest to tylko jeden sposób uzyskiwania dostępu do usługi WCF. Istnieje również możliwość uzyskania dostępu do usługi przy użyciu innych klas .NET Framework, takich jak WCF fabryki kanałów i <xref:System.Net.WebClient>. Inne przykłady w zestawie SDK (takie jak [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki i [automatyczne wybieranie formatu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) przykładowy) pokazują, jak używać tych klas do komunikowania się z usługą WCF.  
  
 W tym przykładzie składa się z 3 projektów:  
  
 Usługa  
 Projekt aplikacji sieci Web, która obejmuje usługi HTTP programu WCF hostowanych w programie ASP.NET.  
  
 Klient  
 Projekt aplikacji konsoli, która sprawia, że wywołań do usługi.  
  
 Wspólne  
 Biblioteki udostępnionej, która zawiera `Customer` typ używany przez klienta i usługi. Po uruchomieniu aplikacji konsolowej klienta klient wysyła żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie na potrzeby przykładu integracji trasy ASP.NET w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Jeśli nie jest jeszcze otwarty, naciśnij klawisz "CTRL + W, S" Aby otworzyć **Eksploratora rozwiązań** okna.  
  
4.  Z **Eksploratora rozwiązań** systemu windows, kliknij prawym przyciskiem myszy **usługi** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **Start Nowe wystąpienie** zostanie wyświetlone menu kontekstowe i wybierz **Uruchom nowe wystąpienie**.  Spowoduje to uruchomienie oprogramowania ASP.NET development server, który hostuje usługę.  
  
5.  Z **Eksploratora rozwiązań** systemu windows, kliknij prawym przyciskiem myszy **klienta** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowy Wystąpienie** zostanie wyświetlone menu kontekstowe i wybierz **Uruchom nowe wystąpienie**.  
  
6.  Okna konsoli klienta pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce. Po uruchomieniu przykładu klienta zapisuje stan bieżącego działania.  
  
7.  Naciśnij dowolny klawisz, aby zakończyć aplikację konsoli klienta.  
  
8.  Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie usługi w obszarze powiadomień Windows kliknij prawym przyciskiem myszy ikonę serwera rozwoju platformy ASP.NET i wybierz pozycję **zatrzymać** z menu kontekstowego.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Zobacz też
