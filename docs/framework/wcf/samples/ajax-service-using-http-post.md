---
title: Usługa AJAX używająca żądań POST protokołu HTTP
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c102d9d403cefb1bf3d4ab75859a81172895c2e0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041112"
---
# <a name="ajax-service-using-http-post"></a>Usługa AJAX używająca żądań POST protokołu HTTP
W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronicznego języka JavaScript i XML (technologia AJAX) usługą, która używa metody POST protokołu HTTP. Usługa AJAX to taki, który możesz uzyskać dostęp przy użyciu podstawowego kodu JavaScript w kliencie przeglądarki sieci Web. W tym przykładzie opiera się na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) Przykładowe; Jedyną różnicą między dwa przykłady jest użycie metody POST protokołu HTTP zamiast HTTP GET.  
  
 Obsługa technologii AJAX w Windows Communication Foundation (WCF) została zoptymalizowana do użytku przy użyciu rozszerzeń ASP.NET AJAX za pośrednictwem `ScriptManager` kontroli. Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Usługa w poniższym przykładzie jest usługi WCF nie kodu specyficznego dla technologii AJAX.  
  
 Jeśli <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut jest stosowany w przypadku operacji lub <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, czasownik HTTP domyślnej ("POST") jest używany. Żądania POST jest trudniejsze do konstruowania niż żądania GET, ale nie są buforowane; Użyj żądania POST dla wszystkich operacji, w których pamięci podręcznej nie jest odpowiednie.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>— podobnie jak w przykładzie podstawowa usługa AJAX.  
  
 Inaczej niż w przypadku żądania GET nie można wywołać usługi WPIS w przeglądarce. Na przykład, przechodząc do http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 powoduje błąd, ponieważ usługa WPIS oczekuje `n1` i `n2` parametrów do wysłania w treści wiadomości — w formacie JSON — a nie w adresie URL.  
  
 Klient PostAjaxClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET, aby wywołać usługę, gdy użytkownik kliknie jeden z przycisków operacji na tej stronie. Usługa odpowiada w taki sam sposób jak w [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki, przy użyciu żądania GET.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano instrukcje dotyczące konfigurowania [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie PostAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Przejdź do http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (nie należy otwierać PostAjaxClientPage.aspx w przeglądarce z katalogu projektu).  
  
## <a name="see-also"></a>Zobacz też
