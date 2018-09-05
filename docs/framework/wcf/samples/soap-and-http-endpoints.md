---
title: Punkty końcowe protokołów SOAP i HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: be050eecebb050ec41c3d548ea993d9e035e471c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523194"
---
# <a name="soap-and-http-endpoints"></a>Punkty końcowe protokołów SOAP i HTTP
W tym przykładzie pokazano, jak zaimplementować usługę opartego na protokole RPC i udostępnić ją w formacie protokołu SOAP i format "Zwykłego starego kodu XML" (POX) za pomocą modelu programowania w sieci Web WCF. Zobacz [podstawowa usługa HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) próbki, aby uzyskać więcej informacji o wiązaniu HTTP dla usługi. Ten przykład koncentruje się na szczegółowe informacje, które odnoszą się do udostępniania tej samej usługi za pośrednictwem protokołu SOAP i HTTP z użyciem różnych powiązania.  
  
## <a name="demonstrates"></a>Demonstracje  
 Udostępnianie usługi RPC za pośrednictwem protokołu SOAP i HTTP przy użyciu usługi WCF.  
  
## <a name="discussion"></a>Dyskusja  
 Ten przykład zawiera dwa składniki: projekt aplikacji sieci Web (usługa), który zawiera usługi WCF i aplikacji konsoli (klient), który wywołuje operacje usługi za pomocą powiązań protokołu SOAP i HTTP.  
  
 Usługa WCF przedstawia działanie 2-`GetData` i `PutData` — która echo ciąg, który został przekazany jako dane wejściowe. Operacje usługi jest oznaczony za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>. Te atrybuty kontrolować projekcji HTTP tych operacji. Ponadto jest oznaczony za pomocą <xref:System.ServiceModel.OperationContractAttribute>, co pozwala na ujawnianie za pośrednictwem powiązania protokołu SOAP. Usługa `PutData` metoda zgłasza wyjątek <xref:System.ServiceModel.Web.WebFaultException>, który zostaje przesłane ponownie przy użyciu protokołu HTTP, przy użyciu kodu stanu HTTP i pobiera wysyłane z powrotem za pośrednictwem protokołu SOAP, jako protokołu SOAP.  
  
 Plik Web.config służy do konfigurowania usługi WCF z punktami końcowymi 3:  
  
-   Punkt końcowy ~/service.svc/mex, który udostępnia metadane usługi dla dostępu przez klientów opartej na protokole SOAP.  
  
-   Punkt końcowy ~/service.svc/http, która umożliwia klientom dostęp do usługi za pomocą powiązania protokołu HTTP.  
  
-   Punkt końcowy ~/service.svc/soap, który umożliwia klientom dostęp do usługi za pośrednictwem powiązania protokołu HTTP przy użyciu protokołu SOAP.  
  
 Punkt końcowy HTTP jest skonfigurowany przy użyciu <`webHttp`> Standardowy punkt końcowy, który ma `helpEnabled` równa `true`. Co w efekcie Usługa udostępnia stronę pomocy XHTML oparte na ~/service.svc/http/help używanego przez klientów opartych na protokole HTTP można uzyskiwać dostęp do usługi.  
  
 Pokazuje projekt klienta, uzyskiwanie dostępu do usługi przy użyciu serwera proxy protokołu SOAP (wygenerowanych za pośrednictwem **Dodaj odwołanie do usługi**) i uzyskiwania dostępu do usługi za pomocą <xref:System.Net.WebClient>.  
  
 Przykład składa się z usługą hostowanych w sieci Web i aplikacji konsoli. Po uruchomieniu aplikacji konsolowej klienta zgłasza żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie dla przykładowej punktów końcowych HTTP i SOAP.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
3.  Jeśli nie jest jeszcze otwarty, naciśnij klawisze CTRL + W, S, aby otworzyć **Eksploratora rozwiązań** okna.  
  
4.  Z **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy **usługi** projektu, umieść kursor nad **debugowania** menu kontekstowego, aby **uruchomić nowy Wystąpienie** zostanie wyświetlone menu kontekstowe. Kliknij przycisk **Uruchom nowe wystąpienie**. Spowoduje to uruchomienie oprogramowania ASP.NET development server, który hostuje usługę.  
  
5.  Z okna Eksploratora rozwiązań kliknij prawym przyciskiem myszy projekt klienta i umieść kursor nad **debugowania** menu kontekstowego, aby **Uruchom nowe wystąpienie** zostanie wyświetlone menu kontekstowe. Kliknij przycisk **Uruchom nowe wystąpienie**.  
  
6.  Okna konsoli klienta pojawia się i zawiera identyfikator URI uruchomioną usługę i identyfikator URI elementu HTML pomocy strony dla uruchomionej usługi. W dowolnym momencie możesz wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.  
  
7.  Po uruchomieniu przykładu klienta zapisuje stan bieżącego działania.  
  
8.  Naciśnij dowolny klawisz, aby zakończyć aplikację konsoli klienta.  
  
9. Naciśnij klawisze SHIFT + F5, aby zatrzymać debugowanie usługi.  
  
10. W obszarze powiadomień Windows kliknij prawym przyciskiem myszy ikonę serwera rozwoju platformy ASP.NET, a następnie wybierz **zatrzymać** z menu kontekstowego.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
