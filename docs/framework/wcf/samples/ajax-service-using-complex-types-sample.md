---
title: Usługa AJAX korzystająca z typów złożonych — przykład
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: cde7e48d0f0c44d68266d60399ac197d322a42cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002888"
---
# <a name="ajax-service-using-complex-types-sample"></a>Usługa AJAX korzystająca z typów złożonych — przykład
W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia usługi ASP.NET asynchronicznych w języku JavaScript i XML (technologia AJAX), który tworzy wystąpienia typów złożonych i wysyła je między usługą i klienta jako JavaScript Object Notation (JSON). Usługa AJAX dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web. W tym przykładzie opiera się na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.  
  
 Obsługa technologii AJAX w programie WCF jest zoptymalizowany do użytku z programem ASP.NET AJAX za pośrednictwem <xref:System.Web.UI.ScriptManager> kontroli. Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Usługa w poniższym przykładzie jest usługi WCF nie kodu specyficznego dla technologii AJAX. Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, czasownik HTTP domyślnej ("POST") jest używany. Usługa ma jedną operację `DoMath`, która zwraca typ złożony, o nazwie `MathResult`. Typ złożony jest typu kontraktu danych w warstwie standardowa, co obejmuje również nie kodu specyficznego dla technologii AJAX.  

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

 Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>— podobnie jak w przykładzie podstawowa usługa AJAX.  
  
 Klient ComplexTypeClientPage.aspx strony sieci Web zawiera kod ASP.NET i JavaScript, aby wywołać usługę, gdy użytkownik kliknie **wykonać obliczenie** przycisk na stronie. Kod, aby wywołać usługę tworzy treść kodu JSON i wysyła je za pomocą metody POST protokołu HTTP, podobnie jak [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) próbki.  
  
 Po pomyślnym wywołania usługi uzyskujesz dostęp do członków poszczególnych danych (`sum`, `difference`, `product` i `quotient`) w JavaScript wynikowy obiekt.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie ComplexTypeAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Przejdź do `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (nie należy otwierać ComplexTypeClientPage.aspx w przeglądarce z katalogu projektu).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
