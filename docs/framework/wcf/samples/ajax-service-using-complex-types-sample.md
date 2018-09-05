---
title: Usługa AJAX korzystająca z typów złożonych — przykład
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4574e5d33ebed7184e229c71e03496db34a95575
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528288"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="673db-102">Usługa AJAX korzystająca z typów złożonych — przykład</span><span class="sxs-lookup"><span data-stu-id="673db-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="673db-103">W tym przykładzie pokazano, jak używać usług Windows Communication Foundation (WCF) do tworzenia usługi ASP.NET asynchronicznych w języku JavaScript i XML (technologia AJAX), który tworzy wystąpienia typów złożonych i wysyła je między usługą i klienta jako JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="673db-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="673db-104">Usługa AJAX dostęp przy użyciu kodu JavaScript w kliencie przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="673db-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="673db-105">W tym przykładzie opiera się na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="673db-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="673db-106">Obsługa technologii AJAX w programie WCF jest zoptymalizowany do użytku z programem ASP.NET AJAX za pośrednictwem <xref:System.Web.UI.ScriptManager> kontroli.</span><span class="sxs-lookup"><span data-stu-id="673db-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="673db-107">Przykład przy użyciu usługi WCF przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="673db-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="673db-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="673db-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="673db-109">Usługa w poniższym przykładzie jest usługi WCF nie kodu specyficznego dla technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="673db-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="673db-110">Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, czasownik HTTP domyślnej ("POST") jest używany.</span><span class="sxs-lookup"><span data-stu-id="673db-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="673db-111">Usługa ma jedną operację `DoMath`, która zwraca typ złożony, o nazwie `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="673db-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="673db-112">Typ złożony jest typu kontraktu danych w warstwie standardowa, co obejmuje również nie kodu specyficznego dla technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="673db-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

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

 <span data-ttu-id="673db-113">Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>— podobnie jak w przykładzie podstawowa usługa AJAX.</span><span class="sxs-lookup"><span data-stu-id="673db-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="673db-114">Klient ComplexTypeClientPage.aspx strony sieci Web zawiera kod ASP.NET i JavaScript, aby wywołać usługę, gdy użytkownik kliknie **wykonać obliczenie** przycisk na stronie.</span><span class="sxs-lookup"><span data-stu-id="673db-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="673db-115">Kod, aby wywołać usługę tworzy treść kodu JSON i wysyła je za pomocą metody POST protokołu HTTP, podobnie jak [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="673db-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="673db-116">Po pomyślnym wywołania usługi uzyskujesz dostęp do członków poszczególnych danych (`sum`, `difference`, `product` i `quotient`) w JavaScript wynikowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="673db-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="673db-117">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="673db-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="673db-118">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="673db-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="673db-119">Skompiluj rozwiązanie ComplexTypeAjaxService.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="673db-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="673db-120">Przejdź do http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (nie należy otwierać ComplexTypeClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="673db-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="673db-121">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="673db-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="673db-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="673db-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="673db-123">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="673db-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="673db-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="673db-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="673db-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="673db-125">See Also</span></span>  
 [<span data-ttu-id="673db-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="673db-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
