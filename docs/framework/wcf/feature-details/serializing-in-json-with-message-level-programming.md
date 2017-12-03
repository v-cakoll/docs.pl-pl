---
title: Serializacja notacji JSON w przypadku programowania na poziomie komunikatu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3967cd7002af8ff9aee4c4f25bd2422d2d0ea1ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="3403e-102">Serializacja notacji JSON w przypadku programowania na poziomie komunikatu</span><span class="sxs-lookup"><span data-stu-id="3403e-102">Serializing in Json with Message Level Programming</span></span>
<span data-ttu-id="3403e-103">Usługi WCF obsługuje serializacji danych w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="3403e-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="3403e-104">W tym temacie opisano, jak sprawdzić WCF do serializacji z typów, za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="3403e-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="3403e-105">Wpisany komunikat programowania</span><span class="sxs-lookup"><span data-stu-id="3403e-105">Typed Message Programming</span></span>  
 <span data-ttu-id="3403e-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Służy po <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> jest stosowany do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3403e-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="3403e-107">Oba te atrybuty umożliwiają określenie `RequestFormat` i `ResponseFormat`.</span><span class="sxs-lookup"><span data-stu-id="3403e-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="3403e-108">Aby używać JSON dla żądań i odpowiedzi Ustaw oba te do `WebMessageFormat.Json`.</span><span class="sxs-lookup"><span data-stu-id="3403e-108">To use JSON for requests and responses set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="3403e-109">Aby można było używać JSON, należy użyć <xref:System.ServiceModel.WebHttpBinding> którego automatycznie konfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3403e-109">In order to use JSON you must use the <xref:System.ServiceModel.WebHttpBinding> which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="3403e-110">Aby uzyskać więcej informacji na temat serializacji WCF, zobacz: [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [szeregowanie programu Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span><span class="sxs-lookup"><span data-stu-id="3403e-110">For more information about WCF serialization, see: [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Serialization in Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span></span> <span data-ttu-id="3403e-111">Aby uzyskać więcej informacji na temat formatu JSON i WCF zobacz [wprowadzenie do usług RESTfull z programem WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [włączone JSON tworzenie usług WCF w .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), i [omówienie REST w programie WCF](http://msdn.microsoft.com/netframework/dd547388).</span><span class="sxs-lookup"><span data-stu-id="3403e-111">For more information about JSON and WCF see [An Introduction to RESTfull Services with WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Creating JSON-enabled WCF Services in .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), and [Overview of REST in WCF](http://msdn.microsoft.com/netframework/dd547388).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3403e-112">Przy użyciu wymaga użycia <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> nie obsługują komunikację protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3403e-112">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="3403e-113">Usługi, które komunikują się z <xref:System.ServiceModel.WebHttpBinding> nie obsługują uwidaczniającą metadanych usługi, więc nie można wygenerować serwer proxy po stronie klienta za pomocą funkcji Dodaj odwołanie do usługi Visual Studio lub narzędzie wiersza polecenia narzędzia svcutil.</span><span class="sxs-lookup"><span data-stu-id="3403e-113">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="3403e-114">Aby uzyskać więcej informacji, jak programowo można wywołać usługi używające <xref:System.ServiceModel.WebHttpBinding>, zobacz [jak korzystać z usługi REST z programem WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span><span class="sxs-lookup"><span data-stu-id="3403e-114">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="3403e-115">Programowanie komunikat bez typu</span><span class="sxs-lookup"><span data-stu-id="3403e-115">Untyped Message Programming</span></span>  
 <span data-ttu-id="3403e-116">Podczas pracy bezpośrednio z obiektów komunikat bez typu, musisz jawnie ustawić właściwości na komunikat bez do serializacji go w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="3403e-116">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="3403e-117">Poniższy fragment kodu pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="3403e-117">The following code snippet shows how to do this.</span></span>  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="3403e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3403e-118">See Also</span></span>  
 [<span data-ttu-id="3403e-119">Integracji AJAX i obsługi JSON</span><span class="sxs-lookup"><span data-stu-id="3403e-119">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="3403e-120">Autonomiczna serializacja kodu JSON</span><span class="sxs-lookup"><span data-stu-id="3403e-120">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="3403e-121">Serializacja JSON</span><span class="sxs-lookup"><span data-stu-id="3403e-121">JSON Serialization</span></span>](../../../../docs/framework/wcf/samples/json-serialization.md)
