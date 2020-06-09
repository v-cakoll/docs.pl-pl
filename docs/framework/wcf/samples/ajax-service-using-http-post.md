---
title: Usługa AJAX używająca żądań POST protokołu HTTP
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 143585b40a493983b7265971a17224165de6f36d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575891"
---
# <a name="ajax-service-using-http-post"></a>Usługa AJAX używająca żądań POST protokołu HTTP

Ten przykład pokazuje, jak używać programu Windows Communication Foundation (WCF) do tworzenia asynchronicznej usługi ASP.NET w języku JavaScript i XML (AJAX) używającej protokołu HTTP POST. Usługa AJAX jest taka, do której można uzyskać dostęp za pomocą podstawowego kodu JavaScript z klienta przeglądarki sieci Web. Ten przykład kompiluje na [podstawowej próbce usługi AJAX](basic-ajax-service.md) ; Jedyną różnicą między tymi dwoma próbkami jest użycie polecenia HTTP POST zamiast HTTP GET.

Obsługa technologii AJAX w Windows Communication Foundation (WCF) jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez `ScriptManager` formant. Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax-service-using-http-post.md).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Usługa w poniższym przykładzie jest usługą WCF bez kodu specyficznego dla technologii AJAX.

Jeśli <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut jest stosowany w operacji lub <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie jest stosowany, zostanie użyte domyślne zlecenie http ("post"). Żądania POST są trudniejsze do skonstruowania niż żądania GET, ale nie są buforowane. Użyj żądań POST dla wszystkich operacji, gdzie buforowanie jest nieodpowiednie.

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Utwórz punkt końcowy AJAX w usłudze przy użyciu programu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , podobnie jak w przypadku przykładowej podstawowej usługi AJAX.

W przeciwieństwie do żądań GET nie można wywoływać usług POST z przeglądarki. Na przykład przechodzenie do `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` powoduje wystąpienie błędu, ponieważ usługa post oczekuje, że `n1` `n2` Parametry i mają być wysyłane w treści wiadomości w formacie JSON, a nie w adresie URL.

Strona sieci Web klienta PostAjaxClientPage. aspx zawiera kod ASP.NET do wywołania usługi za każdym razem, gdy użytkownik kliknie jeden z przycisków operacji na stronie. Usługa reaguje w taki sam sposób jak w przypadku podstawowego przykładowej [usługi AJAX](basic-ajax-service.md) z żądaniem get.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że zostały wykonane instrukcje konfiguracji [jednorazowej procedury konfiguracji dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Skompiluj rozwiązanie PostAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Przejdź do `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (nie otwieraj PostAjaxClientPage. aspx w przeglądarce z katalogu projektu).
