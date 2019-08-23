---
title: Usługa AJAX korzystająca z typów złożonych — przykład
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 98d33c250be31ac43eef6d76ade997a30af87090
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923693"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="d80f8-102">Usługa AJAX korzystająca z typów złożonych — przykład</span><span class="sxs-lookup"><span data-stu-id="d80f8-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="d80f8-103">Ten przykład pokazuje, jak używać Windows Communication Foundation (WCF) do tworzenia asynchronicznej usługi JavaScript i XML (AJAX), która tworzy wystąpienia typów złożonych i wysyła je między usługą a klientem jako JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="d80f8-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="d80f8-104">Dostęp do usługi AJAX można uzyskać za pomocą kodu JavaScript z klienta przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d80f8-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="d80f8-105">Ten przykład kompiluje się na [podstawowym przykładzie usługi AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="d80f8-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="d80f8-106">Obsługa technologii AJAX w programie WCF jest zoptymalizowana pod kątem użycia z <xref:System.Web.UI.ScriptManager> ASP.NET AJAX przez formant.</span><span class="sxs-lookup"><span data-stu-id="d80f8-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="d80f8-107">Aby zapoznać się z przykładem użycia programu WCF z ASP.NET AJAX, zobacz [przykłady AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="d80f8-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d80f8-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d80f8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d80f8-109">Usługa w poniższym przykładzie jest usługą WCF bez kodu specyficznego dla technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="d80f8-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="d80f8-110"><xref:System.ServiceModel.Web.WebGetAttribute> Ponieważ atrybut nie jest stosowany, zostanie użyte domyślne zlecenie http ("post").</span><span class="sxs-lookup"><span data-stu-id="d80f8-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="d80f8-111">Usługa ma jedną operację, `DoMath`która zwraca typ złożony o nazwie. `MathResult`</span><span class="sxs-lookup"><span data-stu-id="d80f8-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="d80f8-112">Typ złożony jest standardowym typem kontraktu danych, który również nie zawiera kodu specyficznego dla AJAX.</span><span class="sxs-lookup"><span data-stu-id="d80f8-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

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

 <span data-ttu-id="d80f8-113">Utwórz punkt końcowy AJAX w usłudze przy użyciu programu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, podobnie jak w przypadku przykładowej podstawowej usługi AJAX.</span><span class="sxs-lookup"><span data-stu-id="d80f8-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="d80f8-114">Strona sieci Web klienta ComplexTypeClientPage. aspx zawiera kod ASP.NET i JavaScript służący do wywoływania usługi, gdy użytkownik kliknie przycisk **wykonaj obliczenia** na stronie.</span><span class="sxs-lookup"><span data-stu-id="d80f8-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="d80f8-115">Kod do wywołania usługi konstruuje treść JSON i wysyła go przy użyciu polecenia HTTP POST, podobnie jak w przypadku [usługi AJAX używającej przykładowego protokołu HTTP Post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="d80f8-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="d80f8-116">Po pomyślnym wywołaniu usługi można uzyskać dostęp do poszczególnych elementów członkowskich danych (`sum` `product` , `difference`i `quotient`) w wyniku obiektu JavaScript.</span><span class="sxs-lookup"><span data-stu-id="d80f8-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d80f8-117">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d80f8-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d80f8-118">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d80f8-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d80f8-119">Skompiluj rozwiązanie ComplexTypeAjaxService. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d80f8-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d80f8-120">Przejdź do `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (nie otwieraj ComplexTypeClientPage. aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="d80f8-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d80f8-121">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d80f8-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d80f8-122">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d80f8-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d80f8-123">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d80f8-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d80f8-124">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d80f8-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="d80f8-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d80f8-125">See also</span></span>

- [<span data-ttu-id="d80f8-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="d80f8-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
