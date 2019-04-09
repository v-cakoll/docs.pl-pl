---
title: Podstawowa usługa AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 8bcfb9a751670d3d1c32de6d8e6f7dc1b84ea30d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147003"
---
# <a name="basic-ajax-service"></a>Podstawowa usługa AJAX
W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznych w języku JavaScript i XML (technologia AJAX) (usługa, której będziesz mieć dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web). Używa usługi <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby upewnić się, czy usługa odpowiada na żądania HTTP GET i jest skonfigurowany do używania formatu JavaScript Object Notation (JSON) w danych odpowiedzi.  
  
 Obsługa technologii AJAX w programie WCF jest zoptymalizowany do użytku z programem ASP.NET AJAX za pośrednictwem `ScriptManager` kontroli. Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W poniższym kodzie <xref:System.ServiceModel.Web.WebGetAttribute> atrybut jest stosowany do `Add` operację, aby upewnić się, że usługa odpowiada na żądania HTTP GET. Kod używa GET dla uproszczenia (można utworzyć żądanie HTTP GET z dowolnej przeglądarki sieci Web). Pobierz umożliwia również włączyć buforowanie. Żądania HTTP POST jest ustawieniem domyślnym w przypadku braku `WebGetAttribute` atrybutu.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Przykładowy plik .svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, która dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> standardowy punkt końcowy do usługi. Punkt końcowy jest konfigurowana na pusty adres względem plików .svc. Oznacza, że adres usługi `http://localhost/ServiceModelSamples/service.svc`, za pomocą nie dodatkowe sufiksy inna niż nazwa operacji.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Jest wstępnie skonfigurowana, aby udostępnić usługę ze strony klienta ASP.NET AJAX. Poniższej sekcji w pliku Web.config może służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego. Można je usunąć, jeśli nie są wymagane żadne dodatkowe zmiany.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Ustawia domyślny format danych usługi do formatu JSON, a nie XML. Aby wywołać usługę, przejdź do `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` po zakończeniu zestawu się i tworzyć kroki opisane w dalszej części tego tematu. Ta funkcja testowania jest włączona przy użyciu żądania HTTP GET.  
  
 Klient SimpleAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET, aby wywołać usługę, gdy użytkownik kliknie jeden z przycisków operacji na tej stronie. `ScriptManager` Formant jest używany udostępnić serwera proxy do usługi za pośrednictwem języka JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Lokalny serwer proxy zostanie uruchomiony, a operacje są wywoływane, używając następującego kodu JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Jeśli wywołanie usługi zakończy się powodzeniem, kod wywołuje `onSuccess` obsługi i wyniki operacji są wyświetlane w polu tekstowym.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
