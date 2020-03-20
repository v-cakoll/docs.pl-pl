---
title: Punkty końcowe protokołów SOAP i HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144022"
---
# <a name="soap-and-http-endpoints"></a>Punkty końcowe protokołów SOAP i HTTP
W tym przykładzie pokazano, jak zaimplementować usługę opartą na RPC i udostępnić ją w formacie SOAP i "Plain Old XML" (POX) format przy użyciu modelu programowania sieci Web WCF. Zobacz przykład [podstawowej usługi HTTP, aby](../../../../docs/framework/wcf/samples/basic-http-service.md) uzyskać więcej informacji na temat powiązania HTTP dla usługi. W tym przykładzie koncentruje się na szczegóły, które odnoszą się do uwidaczniania tej samej usługi za pośrednictwem protokołu SOAP i HTTP przy użyciu różnych powiązań.  
  
## <a name="demonstrates"></a>Demonstracje  
 Udostępnianie usługi RPC za pośrednictwem protokołu SOAP i HTTP przy użyciu WCF.  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład składa się z dwóch składników: projektu aplikacji sieci Web (usługa), który zawiera usługę WCF i aplikacji konsoli (klient), która wywołuje operacje usługi przy użyciu powiązań PROTOKOŁU SOAP i HTTP.  
  
 Usługa WCF udostępnia 2`GetData` operacji `PutData` — i — że echo ciąg, który został przekazany jako dane wejściowe. Operacje usługi są opisywane <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute>z . Te atrybuty kontrolują projekcję HTTP tych operacji. Ponadto, są one oznaczone <xref:System.ServiceModel.OperationContractAttribute>, co pozwala na ich narażenie na wiązania SOAP. `PutData` Metoda usługi zgłasza <xref:System.ServiceModel.Web.WebFaultException>, który jest wysyłany z powrotem za pośrednictwem protokołu HTTP przy użyciu kodu stanu HTTP i jest wysyłany z powrotem przez SOAP jako błąd PROTOKOŁU SOAP.  
  
 Plik Web.config konfiguruje usługę WCF z 3 punktami końcowymi:  
  
- Punkt końcowy ~/service.svc/mex, który udostępnia metadane usługi w celu uzyskania dostępu przez klientów opartych na posłudze SOAP.  
  
- ~/service.svc/http punktu końcowego, który umożliwia klientom dostęp do usługi przy użyciu powiązania HTTP.  
  
- ~/service.svc/soap punkt końcowy, który umożliwia klientom dostęp do usługi przy użyciu powiązania SOAP za pośrednictwem protokołu HTTP.  
  
 Punkt końcowy HTTP jest skonfigurowany z `webHttp` <> standardowego punktu `helpEnabled` końcowego, który został ustawiony na `true`. W rezultacie usługa udostępnia stronę pomocy opartą na języku XHTML w ~/service.svc/http/help, której klienci oparte na protokowi HTTP mogą używać do uzyskiwania dostępu do usługi.  
  
 Projekt klienta demonstruje uzyskiwanie dostępu do usługi przy użyciu serwera proxy SOAP <xref:System.Net.WebClient>(generowanego za pomocą dodaj odwołania do **usługi)** i uzyskiwanie dostępu do usługi przy użyciu .  
  
 Przykład składa się z usługi hostowane w sieci Web i aplikacji konsoli. Po uruchomieniu aplikacji konsoli klient żąda do usługi i zapisuje istotne informacje z odpowiedzi do okna konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić próbkę  
  
1. Otwórz rozwiązanie dla przykładu punktów końcowych PROTOKOŁU SOAP i HTTP.  
  
2. Naciśnij kombinację klawiszy CTRL+SHIFT+B w celu skompilowania rozwiązania.  
  
3. Jeśli nie jest jeszcze otwarty, naciśnij klawisze CTRL+W, S, aby otworzyć okno **Eksploratora rozwiązań.**  
  
4. W oknie **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **usługi** i umieść kursor nad opcją menu kontekstowego **debugowania,** aby było wyświetlane menu kontekstowe **Rozpocznij nowe wystąpienie.** Kliknij **pozycję Rozpocznij nowe wystąpienie**. Spowoduje to uruchomienie serwera dewelopera ASP.NET, który obsługuje usługę.  
  
5. W oknach Eksploratora rozwiązań kliknij prawym przyciskiem myszy projekt Klienta i umieść kursor nad opcją menu kontekstowego **debugowania,** aby było wyświetlane menu kontekstowe **Rozpocznij nowe wystąpienie.** Kliknij **pozycję Rozpocznij nowe wystąpienie**.  
  
6. Zostanie wyświetlona okno konsoli klienta, które udostępnia identyfikator URI uruchomionej usługi oraz identyfikator URI strony pomocy HTML dla uruchomionej usługi. W dowolnym momencie można wyświetlić stronę pomocy HTML, wpisując identyfikator URI strony pomocy w przeglądarce.  
  
7. Po uruchomieniu próbki klient zapisuje stan bieżącego działania.  
  
8. Naciśnij dowolny klawisz, aby zakończyć aplikację konsoli klienckiej.  
  
9. Naciśnij klawisze SHIFT+F5, aby zatrzymać debugowanie usługi.  
  
10. W obszarze powiadomień systemu Windows kliknij prawym przyciskiem myszy ikonę serwera dewelopera ASP.NET i wybierz polecenie **Zatrzymaj** z menu kontekstowego.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
