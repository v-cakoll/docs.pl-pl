---
title: Usługa AJAX korzystająca z typów złożonych — przykład
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4227446e8844accd06490d8e7cf933da43d875a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575917"
---
# <a name="ajax-service-using-complex-types-sample"></a>Usługa AJAX korzystająca z typów złożonych — przykład

Ten przykład pokazuje, jak używać Windows Communication Foundation (WCF) do tworzenia asynchronicznej usługi JavaScript i XML (AJAX), która tworzy wystąpienia typów złożonych i wysyła je między usługą a klientem jako JavaScript Object Notation (JSON). Dostęp do usługi AJAX można uzyskać za pomocą kodu JavaScript z klienta przeglądarki sieci Web. Ten przykład kompiluje się na [podstawowym przykładzie usługi AJAX](basic-ajax-service.md) .

Obsługa technologii AJAX w programie WCF jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez <xref:System.Web.UI.ScriptManager> formant. Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Usługa w poniższym przykładzie jest usługą WCF bez kodu specyficznego dla technologii AJAX. Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie jest stosowany, zostanie użyte domyślne zlecenie http ("post"). Usługa ma jedną operację, `DoMath` która zwraca typ złożony o nazwie `MathResult` . Typ złożony jest standardowym typem kontraktu danych, który również nie zawiera kodu specyficznego dla AJAX.

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

Utwórz punkt końcowy AJAX w usłudze przy użyciu programu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , podobnie jak w przypadku przykładowej podstawowej usługi AJAX.

Strona sieci Web klienta ComplexTypeClientPage. aspx zawiera kod ASP.NET i JavaScript służący do wywoływania usługi, gdy użytkownik kliknie przycisk **wykonaj obliczenia** na stronie. Kod do wywołania usługi konstruuje treść JSON i wysyła go przy użyciu polecenia HTTP POST, podobnie jak w przypadku [usługi AJAX używającej przykładowego protokołu HTTP Post](ajax-service-using-http-post.md) .

Po pomyślnym wywołaniu usługi można uzyskać dostęp do poszczególnych elementów członkowskich danych ( `sum` , `difference` `product` i `quotient` ) w wyniku obiektu JavaScript.

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Skompiluj rozwiązanie ComplexTypeAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Przejdź do `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (nie otwieraj ComplexTypeClientPage. aspx w przeglądarce z katalogu projektu).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a>Zobacz też

- [Podstawowa usługa AJAX](basic-ajax-service.md)
