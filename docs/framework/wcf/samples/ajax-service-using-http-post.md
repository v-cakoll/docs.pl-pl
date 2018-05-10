---
title: Usługa AJAX używająca żądań POST protokołu HTTP
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-using-http-post"></a>Usługa AJAX używająca żądań POST protokołu HTTP
W tym przykładzie pokazano, jak używać usługi Windows Communication Foundation (WCF) do tworzenia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronicznego JavaScript i XML (AJAX) usługa, która używa metody POST protokołu HTTP. Usługa AJAX to takie, które są dostępne przy użyciu podstawowego kodu JavaScript w kliencie przeglądarki sieci Web. Ten przykład jest oparty na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) przykładowa; jedyną różnicą między dwoma próbki jest użycie metody POST protokołu HTTP zamiast HTTP GET.  
  
 Obsługa interfejsu AJAX w systemie Windows Communication Foundation (WCF) jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem `ScriptManager` formantu. Na przykład przy użyciu programu WCF z ASP.NET AJAX, zobacz [przykłady Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Usługi w poniższym przykładzie jest usługi WCF za pomocą kodu nie AJAX.  
  
 Jeśli <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut jest stosowany w przypadku operacji lub <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, jest używany domyślny zlecenie HTTP ("POST"). Żądania POST jest utrudnione do skonstruowania niż żądania GET, ale nie są buforowane; Użyj żądania POST dla wszystkich operacji, gdy buforowanie nie jest odpowiedni.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, po prostu tak jak na przykład podstawowa usługa AJAX.  
  
 W przeciwieństwie do żądania GET nie można wywołać usługi POST z przeglądarki. Na przykład, przechodząc do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 zakończy się błędem, ponieważ usługa POST oczekuje `n1` i `n2` parametrów do wysłania w treści wiadomości — w formacie JSON —, a nie w adresie URL.  
  
 Klient PostAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET można wywołać usługi, gdy użytkownik kliknie jeden z przycisków operacji na stronie. Usługa odpowiada w taki sam sposób jak w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki z żądania GET.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonać instrukcje dotyczące instalacji [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie PostAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (nie należy otwierać PostAjaxClientPage.aspx w przeglądarce z katalogu projektu).  
  
## <a name="see-also"></a>Zobacz też
