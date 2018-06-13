---
title: Podstawowa usługa AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 0bb8a2b28ea87cb0c22126540f6cdab604ca5120
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805983"
---
# <a name="basic-ajax-service"></a>Podstawowa usługa AJAX
W tym przykładzie pokazano, jak używać usługi Windows Communication Foundation (WCF) do tworzenia podstawowej usługi ASP.NET asynchronicznego JavaScript i XML (AJAX) (usługa dostęp można uzyskać przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web). Używane przez usługę <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby upewnić się, że usługa odpowiada na żądania HTTP GET i jest skonfigurowana do używania formatu danych JavaScript Object Notation (JSON) na odpowiedzi.  
  
 Obsługa interfejsu AJAX w programie WCF jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu. Na przykład przy użyciu programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W poniższym kodzie <xref:System.ServiceModel.Web.WebGetAttribute> atrybut jest stosowany do `Add` operację, aby upewnić się, że usługa odpowiada na żądania HTTP GET. Kod używa operacji GET dla uproszczenia (można utworzyć żądania HTTP GET z dowolnej przeglądarki sieci Web). Aby włączyć buforowanie umożliwia także GET. HTTP POST jest wartość domyślna w przypadku braku `WebGetAttribute` atrybutu.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 Przykładowy plik .svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, która dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> standardowy punkt końcowy do usługi. Punkt końcowy jest skonfigurowana na pusty adres względem pliku svc. Oznacza to, że adres usługi http://localhost/ServiceModelSamples/service.svc, z nie dodatkowe sufiksy na inną niż nazwa operacji.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> Jest wstępnie skonfigurowana, aby udostępnić usługę ze strony klienta ASP.NET AJAX. Następujących sekcji w pliku Web.config mogą służyć do wprowadzenia dodatkowych zmian konfiguracyjnych do punktu końcowego. Można usunąć, jeśli są wymagane nie dodatkowe zmiany.  
  
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
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Ustawia domyślny format danych usługi do formatu JSON, a nie XML. Aby wywołać usługę, przejdź do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 po zakończeniu zestaw się i kompilacji kroki opisane w dalszej części tego tematu. Ta funkcja testowania jest włączona za pomocą żądania HTTP GET.  
  
 Klient SimpleAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET można wywołać usługi, gdy użytkownik kliknie jeden z przycisków operacji na stronie. `ScriptManager` Kontrola służy do udostępnić serwer proxy do usługi za pomocą skryptu JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 Lokalny serwer proxy zostanie uruchomiony i operacje są wywoływane przy użyciu następującego kodu JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Jeśli wywołanie usługi zakończy się powodzeniem, kod wywołuje `onSuccess` obsługi i wyniku operacji jest wyświetlana w polu tekstowym.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Zobacz też
