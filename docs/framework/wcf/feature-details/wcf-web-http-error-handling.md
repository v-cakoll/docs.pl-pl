---
title: Obsługa błędów protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 834c642e36e1551081dbe1f14529ed7596df1360
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152701"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="47838-102">Obsługa błędów protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="47838-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="47838-103">Obsługa błędów protokołu HTTP sieci Web Windows Communication Foundation (WCF) pozwala zwrócić błędy z usług WCF Web HTTP, które określić kod stanu HTTP i zwraca szczegóły błędu przy użyciu tego samego formatu co operacji (na przykład XML lub JSON).</span><span class="sxs-lookup"><span data-stu-id="47838-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="47838-104">Obsługa błędów protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="47838-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="47838-105"><xref:System.ServiceModel.Web.WebFaultException> Klasa definiuje konstruktora, który pozwala określić kod stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="47838-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="47838-106">Ten kod stanu jest zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="47838-106">This status code is then returned to the client.</span></span> <span data-ttu-id="47838-107">Ogólny wersję <xref:System.ServiceModel.Web.WebFaultException> klasy <xref:System.ServiceModel.Web.WebFaultException%601> umożliwia zwracają typ zdefiniowany przez użytkownika, który zawiera informacje o błędzie, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="47838-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="47838-108">Ten niestandardowy obiekt jest serializowany, przy użyciu formatu określony przez operację i zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="47838-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="47838-109">Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="47838-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="47838-110">Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP i dodatkowe informacje w typ zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="47838-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> `MyErrorDetail` <span data-ttu-id="47838-111">jest typ zdefiniowany przez użytkownika, który zawiera dodatkowe informacje o błędzie, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="47838-111">is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="47838-112">Powyższy kod zwraca odpowiedź HTTP z kodem stanu zabronione i treści, która zawiera wystąpienie `MyErrorDetails` obiektu.</span><span class="sxs-lookup"><span data-stu-id="47838-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="47838-113">Format `MyErrorDetails` obiektu jest określana przez:</span><span class="sxs-lookup"><span data-stu-id="47838-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="47838-114">Wartość `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu wskazanego w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="47838-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="47838-115">Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="47838-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="47838-116">Wartość <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwości, uzyskując dostęp do <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="47838-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="47838-117">Aby uzyskać więcej informacji na temat wpływu tych wartości na formatowanie operacji, zobacz [WCF Web HTTP formatowanie](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="47838-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <xref:System.ServiceModel.Web.WebFaultException> <span data-ttu-id="47838-118">jest <xref:System.ServiceModel.FaultException> i dlatego może służyć jako model programowania wyjątków błędów dla usług, które uwidaczniają punkty końcowe protokołu SOAP, a także punktów końcowych HTTP w sieci web.</span><span class="sxs-lookup"><span data-stu-id="47838-118">is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47838-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47838-119">See also</span></span>

- [<span data-ttu-id="47838-120">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="47838-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="47838-121">Formatowanie internetowego kodu HTTP w programie WCF</span><span class="sxs-lookup"><span data-stu-id="47838-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="47838-122">Definiowanie i określanie błędów</span><span class="sxs-lookup"><span data-stu-id="47838-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="47838-123">Obsługa wyjątków i błędów</span><span class="sxs-lookup"><span data-stu-id="47838-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="47838-124">Wysyłanie i odbieranie błędów</span><span class="sxs-lookup"><span data-stu-id="47838-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
