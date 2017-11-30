---
title: "Obsługa błędów protokołu HTTP sieci Web w programie WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3366ab851c6e6b66a5df94bdb24baad4ae0c8d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="4baf6-102">Obsługa błędów protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="4baf6-102">WCF Web HTTP Error Handling</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="4baf6-103">Obsługa błędów protokołu HTTP sieci Web umożliwia zwracanie błędów z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług HTTP w sieci Web, określające stan HTTP kodu i zwracać szczegóły błędu przy użyciu tego samego formatu co operacji (na przykład, XML lub JSON).</span><span class="sxs-lookup"><span data-stu-id="4baf6-103"> Web HTTP error handling enables you to return errors from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="4baf6-104">Obsługa błędów protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="4baf6-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="4baf6-105"><xref:System.ServiceModel.Web.WebFaultException> Klasa definiuje konstruktora, który pozwala określić kod stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4baf6-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="4baf6-106">Ten kod stanu jest następnie zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="4baf6-106">This status code is then returned to the client.</span></span> <span data-ttu-id="4baf6-107">Ogólny wersji <xref:System.ServiceModel.Web.WebFaultException> klasy <xref:System.ServiceModel.Web.WebFaultException%601> pozwala na zwracany typ zdefiniowane przez użytkownika, który zawiera informacje o błędzie, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="4baf6-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="4baf6-108">Ten obiekt niestandardowy jest serializowany w formacie określonym przez operację i zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="4baf6-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="4baf6-109">Poniższy przykład przedstawia sposób zwrócenia kod stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4baf6-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="4baf6-110">Poniższy przykład przedstawia sposób zwracania kod stanu HTTP i informacje dodatkowe na typu zdefiniowanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4baf6-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="4baf6-111">`MyErrorDetail`jest zdefiniowane przez użytkownika typu, który zawiera dodatkowe informacje o błędzie, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="4baf6-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="4baf6-112">Poprzedni kod zwraca odpowiedź HTTP z kodem stanu niedozwolonych i treści, która zawiera wystąpienie `MyErrorDetails` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4baf6-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="4baf6-113">Format `MyErrorDetails` obiektu jest określane przez:</span><span class="sxs-lookup"><span data-stu-id="4baf6-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="4baf6-114">Wartość `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> określonego w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4baf6-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="4baf6-115">Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="4baf6-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="4baf6-116">Wartość <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwości uzyskując dostęp do <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="4baf6-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4baf6-117">wpływ tych wartości formatowania operacji, zobacz [formatowania HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4baf6-117"> how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="4baf6-118"><xref:System.ServiceModel.Web.WebFaultException>jest <xref:System.ServiceModel.FaultException> i w związku z tym może służyć jako model programowania wyjątek błędów dla usług, które ekspozycji punktów końcowych SOAP, a także punktów końcowych HTTP w sieci web.</span><span class="sxs-lookup"><span data-stu-id="4baf6-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4baf6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4baf6-119">See Also</span></span>  
 [<span data-ttu-id="4baf6-120">Model programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="4baf6-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="4baf6-121">Formatowanie kodu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="4baf6-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [<span data-ttu-id="4baf6-122">Definiowanie i określanie błędów</span><span class="sxs-lookup"><span data-stu-id="4baf6-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [<span data-ttu-id="4baf6-123">Obsługa wyjątków i błędów</span><span class="sxs-lookup"><span data-stu-id="4baf6-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [<span data-ttu-id="4baf6-124">Wysyłanie i odbieranie błędów</span><span class="sxs-lookup"><span data-stu-id="4baf6-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
