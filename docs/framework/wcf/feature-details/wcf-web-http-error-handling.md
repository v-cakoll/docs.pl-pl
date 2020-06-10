---
title: Obsługa błędów protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: b1d41bebafa2795d390b120ad84475417389479b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598648"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="5f399-102">Obsługa błędów protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="5f399-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="5f399-103">Obsługa błędów HTTP sieci Web w programie Windows Communication Foundation (WCF) umożliwia zwracanie błędów z usług HTTP sieci Web w programie WCF, które określają kod stanu HTTP i zwracają szczegóły błędu przy użyciu tego samego formatu co operacja (na przykład XML lub JSON).</span><span class="sxs-lookup"><span data-stu-id="5f399-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="5f399-104">Obsługa błędów protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="5f399-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="5f399-105"><xref:System.ServiceModel.Web.WebFaultException>Klasa definiuje konstruktora, który umożliwia określenie kodu stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5f399-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="5f399-106">Ten kod stanu jest następnie zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="5f399-106">This status code is then returned to the client.</span></span> <span data-ttu-id="5f399-107">Ogólna wersja <xref:System.ServiceModel.Web.WebFaultException> klasy, <xref:System.ServiceModel.Web.WebFaultException%601> umożliwia zwrócenie typu zdefiniowanego przez użytkownika, który zawiera informacje o błędzie, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="5f399-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="5f399-108">Ten obiekt niestandardowy jest serializowany przy użyciu formatu określonego przez operację i zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="5f399-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="5f399-109">Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5f399-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="5f399-110">Poniższy przykład pokazuje, jak zwrócić kod stanu HTTP i dodatkowe informacje w typie zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5f399-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="5f399-111">`MyErrorDetail`jest typem zdefiniowanym przez użytkownika, który zawiera dodatkowe informacje o błędzie, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="5f399-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="5f399-112">Poprzedni kod zwraca odpowiedź HTTP z niedozwolonym kodem stanu i treścią zawierającą wystąpienie `MyErrorDetails` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5f399-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="5f399-113">Format `MyErrorDetails` obiektu jest określany przez:</span><span class="sxs-lookup"><span data-stu-id="5f399-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="5f399-114">Wartość `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu określonego w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5f399-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="5f399-115">Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> .</span><span class="sxs-lookup"><span data-stu-id="5f399-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="5f399-116">Wartość <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Właściwości przez uzyskanie dostępu do elementu <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .</span><span class="sxs-lookup"><span data-stu-id="5f399-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="5f399-117">Aby uzyskać więcej informacji o tym, jak te wartości wpływają na formatowanie operacji, zobacz temat [Formatowanie http sieci Web](wcf-web-http-formatting.md)w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="5f399-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="5f399-118"><xref:System.ServiceModel.Web.WebFaultException>jest <xref:System.ServiceModel.FaultException> i dlatego może służyć jako model programowania wyjątku błędów dla usług, które uwidaczniają punkty końcowe protokołu SOAP, a także punkty końcowe http sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5f399-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f399-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f399-119">See also</span></span>

- [<span data-ttu-id="5f399-120">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="5f399-120">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="5f399-121">Formatowanie kodu HTTP dla sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="5f399-121">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="5f399-122">Definiowanie i określanie błędów</span><span class="sxs-lookup"><span data-stu-id="5f399-122">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="5f399-123">Obsługa wyjątków i błędów</span><span class="sxs-lookup"><span data-stu-id="5f399-123">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="5f399-124">Wysyłanie i odbieranie błędów</span><span class="sxs-lookup"><span data-stu-id="5f399-124">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
