---
title: "Podstawowa usługa AJAX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 540e7d2705dbdd3249a0519efb80de676428e92f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="basic-ajax-service"></a>Podstawowa usługa AJAX
W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] można utworzyć podstawowej usługi ASP.NET asynchronicznego JavaScript i XML (AJAX) (usługa dostęp można uzyskać przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web). Używane przez usługę <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby upewnić się, że usługa odpowiada na żądania HTTP GET i jest skonfigurowana do używania formatu danych JavaScript Object Notation (JSON) na odpowiedzi.  
  
 Obsługa interfejsu AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu. Na przykład za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W poniższym kodzie <xref:System.ServiceModel.Web.WebGetAttribute> atrybut jest stosowany do `Add` operację, aby upewnić się, że usługa odpowiada na żądania HTTP GET. Kod używa operacji GET dla uproszczenia (można utworzyć żądania HTTP GET z dowolnej przeglądarki sieci Web). Aby włączyć buforowanie umożliwia także GET. HTTP POST jest wartość domyślna w przypadku braku `WebGetAttribute` atrybutu.  
  
```  
[ServiceContract(Namespace = "SimpleAjaxService")]  
public interface ICalculator  
{  
  
    [WebGet]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}  
```  
  
 Przykładowy plik .svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, która dodaje <xref:System.ServiceModel.Description.WebScriptEndpoint> standardowy punkt końcowy do usługi. Punkt końcowy jest skonfigurowana na pusty adres względem pliku svc. Oznacza to, że adres usługi ma http://localhost/ServiceModelSamples/service.svc z nie dodatkowe sufiksy na inną niż nazwa operacji.  
  
```  
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
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> Ustawia domyślny format danych usługi do formatu JSON, a nie XML. Aby wywołać usługę, przejdź do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 po zakończeniu zestawu w górę i kompilacji kroki opisane w dalszej części tego tematu. Ta funkcja testowania jest włączona za pomocą żądania HTTP GET.  
  
 Klient SimpleAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET można wywołać usługi, gdy użytkownik kliknie jeden z przycisków operacji na stronie. `ScriptManager` Kontrola służy do udostępnić serwer proxy do usługi za pomocą skryptu JavaScript.  
  
```  
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```  
  
 Lokalny serwer proxy zostanie uruchomiony i operacje są wywoływane przy użyciu następującego kodu JavaScript.  
  
```  
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```  
  
 Jeśli wywołanie usługi zakończy się powodzeniem, kod wywołuje `onSuccess` obsługi i wyniku operacji jest wyświetlana w polu tekstowym.  
  
```  
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}  
```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Zobacz też
