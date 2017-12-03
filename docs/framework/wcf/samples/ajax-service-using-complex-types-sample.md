---
title: "Usługa AJAX korzystająca z typów złożonych — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d071bf182fb231b08f397db163059fda730fca21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="16c5d-102">Usługa AJAX korzystająca z typów złożonych — przykład</span><span class="sxs-lookup"><span data-stu-id="16c5d-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="16c5d-103">W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Aby utworzyć usługę ASP.NET asynchronicznego JavaScript i XML (AJAX), która tworzy wystąpienia typów złożonych i wysyła je między usługą i klienta jako JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="16c5d-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="16c5d-104">Usługa AJAX mogą korzystać za pomocą kodu JavaScript w kliencie przeglądarki sieci Web.</span><span class="sxs-lookup"><span data-stu-id="16c5d-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="16c5d-105">Ten przykład jest oparty na [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="16c5d-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="16c5d-106">Obsługa interfejsu AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX za pośrednictwem <xref:System.Web.UI.ScriptManager> formantu.</span><span class="sxs-lookup"><span data-stu-id="16c5d-106">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="16c5d-107">Na przykład za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="16c5d-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16c5d-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="16c5d-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="16c5d-109">Usługi w poniższym przykładzie jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z żadnego kodu specyficzne dla interfejsu AJAX.</span><span class="sxs-lookup"><span data-stu-id="16c5d-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span> <span data-ttu-id="16c5d-110">Ponieważ <xref:System.ServiceModel.Web.WebGetAttribute> atrybut nie ma zastosowania, jest używany domyślny zlecenie HTTP ("POST").</span><span class="sxs-lookup"><span data-stu-id="16c5d-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="16c5d-111">Usługa ma jedną operację `DoMath`, która zwraca wartość typu złożonego o nazwie `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="16c5d-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="16c5d-112">Typ złożony jest typu kontraktu danych standardowe, które również nie zawiera określonego AJAX kodu.</span><span class="sxs-lookup"><span data-stu-id="16c5d-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  
  
```  
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
  
 <span data-ttu-id="16c5d-113">Tworzenie punktu końcowego AJAX w usłudze przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, po prostu tak jak na przykład podstawowa usługa AJAX.</span><span class="sxs-lookup"><span data-stu-id="16c5d-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="16c5d-114">Klient ComplexTypeClientPage.aspx strony sieci Web zawiera kod platformy ASP.NET i JavaScript do wywołania usługi, gdy użytkownik kliknie **obliczanie** przycisk na stronie.</span><span class="sxs-lookup"><span data-stu-id="16c5d-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="16c5d-115">Kod, aby wywołać usługę konstruuje treść kodu JSON i wysyła je przy użyciu protokołu HTTP POST, podobnie jak [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="16c5d-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="16c5d-116">Po wywołaniu usługi zakończy się powodzeniem, można uzyskać dostępu do elementów członkowskich danych poszczególnych (`sum`, `difference`, `product` i `quotient`) na JavaScript wynikowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="16c5d-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="16c5d-117">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="16c5d-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="16c5d-118">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16c5d-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="16c5d-119">Skompiluj rozwiązanie ComplexTypeAjaxService.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16c5d-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="16c5d-120">Przejdź do http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (nie należy otwierać ComplexTypeClientPage.aspx w przeglądarce z katalogu projektu).</span><span class="sxs-lookup"><span data-stu-id="16c5d-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16c5d-121">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="16c5d-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="16c5d-122">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="16c5d-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="16c5d-123">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="16c5d-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16c5d-124">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="16c5d-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="16c5d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16c5d-125">See Also</span></span>  
 [<span data-ttu-id="16c5d-126">Podstawowa usługa AJAX</span><span class="sxs-lookup"><span data-stu-id="16c5d-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
