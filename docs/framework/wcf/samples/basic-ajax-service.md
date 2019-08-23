---
title: Podstawowa usługa AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 2d3770630df693093b05868f00c409f8245f858b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925238"
---
# <a name="basic-ajax-service"></a>Podstawowa usługa AJAX
Ten przykład pokazuje, jak używać programu Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznej języka JavaScript i XML (AJAX) (usługi, do której można uzyskać dostęp za pomocą kodu JavaScript z klienta przeglądarki sieci Web). Usługa używa atrybutu, <xref:System.ServiceModel.Web.WebGetAttribute> aby upewnić się, że usługa odpowiada na żądania HTTP GET i jest skonfigurowana do używania formatu danych JavaScript Object Notation (JSON) dla odpowiedzi.  
  
 Obsługa technologii AJAX w programie WCF jest zoptymalizowana pod kątem użycia z `ScriptManager` ASP.NET AJAX przez formant. Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W poniższym kodzie <xref:System.ServiceModel.Web.WebGetAttribute> atrybut jest stosowany `Add` do operacji, aby upewnić się, że usługa odpowiada na żądania HTTP GET. Kod używa elementu GET for prostoty (można utworzyć żądanie HTTP GET z dowolnej przeglądarki sieci Web). Można również użyć GET, aby włączyć buforowanie. Wpis http post jest wartością domyślną w nieobecności `WebGetAttribute` atrybutu.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Plik Sample. svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, który <xref:System.ServiceModel.Description.WebScriptEndpoint> dodaje standardowy punkt końcowy do usługi. Punkt końcowy jest skonfigurowany z pustym adresem względem pliku SVC. Oznacza to, że adres usługi to `http://localhost/ServiceModelSamples/service.svc`, bez dodatkowych sufiksów innych niż nazwa operacji.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Jest wstępnie skonfigurowany tak, aby usługa była dostępna ze strony klienta AJAX ASP.NET. Poniższa sekcja w pliku Web. config może służyć do wprowadzania dodatkowych zmian w konfiguracji punktu końcowego. Jeśli nie są wymagane żadne dodatkowe zmiany, można je usunąć.  
  
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
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Ustawia domyślny format danych usługi na JSON zamiast XML. Aby wywołać usługę, przejdź do `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` po zakończeniu kroków konfiguracji i kompilacji przedstawionych w dalszej części tego tematu. Ta funkcja testowa jest włączana za pomocą żądania HTTP GET.  
  
 Strona sieci Web klienta SimpleAjaxClientPage. aspx zawiera kod ASP.NET do wywołania usługi za każdym razem, gdy użytkownik kliknie jeden z przycisków operacji na stronie. `ScriptManager` Kontrolka służy do udostępniania serwerowi proxy usługi dostępnego za pomocą języka JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Zostanie utworzone wystąpienie lokalnego serwera proxy, a operacje są wywoływane przy użyciu następującego kodu JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Jeśli wywołanie usługi powiedzie się, kod wywoła `onSuccess` procedurę obsługi, a wynik operacji zostanie wyświetlony w polu tekstowym.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
