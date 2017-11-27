---
title: 'Instrukcje: Ujawnianie kontraktu klientom sieci Web i SOAP'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06127af9c373987c02b2e53ff57e6f50a7f5baa5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="88064-102">Instrukcje: Ujawnianie kontraktu klientom sieci Web i SOAP</span><span class="sxs-lookup"><span data-stu-id="88064-102">How to: Expose a Contract to SOAP and Web Clients</span></span>
<span data-ttu-id="88064-103">Domyślnie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] udostępnia punkty końcowe tylko do klientów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="88064-103">By default, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="88064-104">W [porady: Tworzenie podstawowej usługi HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), punkt końcowy będą dostępne dla klientów z systemem innym niż SOAP.</span><span class="sxs-lookup"><span data-stu-id="88064-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="88064-105">Może to być razy, jeśli chcesz udostępnić ten sam kontrakt obu kierunkach, jako punkt końcowy sieci Web, a punkt końcowy protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="88064-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="88064-106">W tym temacie przedstawiono przykład sposobu wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="88064-106">This topic shows an example of how to do this.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="88064-107">Aby zdefiniować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="88064-107">To define the service contract</span></span>  
  
1.  <span data-ttu-id="88064-108">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="88064-109">Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania operacji POST.</span><span class="sxs-lookup"><span data-stu-id="88064-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="88064-110">Można jednak określić metodę do mapowania na operację, określając "metody =" parametru.</span><span class="sxs-lookup"><span data-stu-id="88064-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="88064-111"><xref:System.ServiceModel.Web.WebGetAttribute>nie ma "metody =" parametru i map tylko GET wywołania do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="88064-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="88064-112">Implementowanie kontraktu usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-112">Implement the service contract, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="88064-113">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="88064-113">To host the service</span></span>  
  
1.  <span data-ttu-id="88064-114">Utwórz <xref:System.ServiceModel.ServiceHost> obiektów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  <span data-ttu-id="88064-115">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.BasicHttpBinding> dla punktu końcowego protokołu SOAP, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  <span data-ttu-id="88064-116">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.WebHttpBinding> dla punktu końcowego z systemem innym niż SOAP i Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  <span data-ttu-id="88064-117">Wywołanie `Open()` na <xref:System.ServiceModel.ServiceHost> wystąpienia można otworzyć hosta usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="88064-118">Do wywołania operacji usługi mapowane na GET w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="88064-118">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="88064-119">Otwórz program Internet Explorer i wpisz "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="88064-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="88064-120">Adres URL zawiera adres podstawowy usługi ("http://localhost: 8000 /"), względny adres punktu końcowego (""), usługi operację wywołania ("EchoWithGet") i znak zapytania następuje lista parametrów nazwanych oddzielonymi znakiem handlowego "i" (&).</span><span class="sxs-lookup"><span data-stu-id="88064-120">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="88064-121">Do wywołania operacji usługi sieci Web w punkcie końcowym w kodzie</span><span class="sxs-lookup"><span data-stu-id="88064-121">To call service operations on the Web endpoint in code</span></span>  
  
1.  <span data-ttu-id="88064-122">Utwórz wystąpienie <xref:System.ServiceModel.Web.WebChannelFactory%601> w `using` zablokować, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="88064-123">`Close()`automatycznie jest wywoływana w kanale na końcu `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="88064-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>  
  
1.  <span data-ttu-id="88064-124">Tworzenie kanału i wywołania tej usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-124">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="88064-125">Do wywołania operacji usługi w punkcie końcowym protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="88064-125">To call service operations on the SOAP endpoint</span></span>  
  
1.  <span data-ttu-id="88064-126">Utwórz wystąpienie <xref:System.ServiceModel.ChannelFactory> w `using` zablokować, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  <span data-ttu-id="88064-127">Tworzenie kanału i wywołania tej usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-127">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a><span data-ttu-id="88064-128">Aby zamknąć hosta usługi</span><span class="sxs-lookup"><span data-stu-id="88064-128">To close the service host</span></span>  
  
1.  <span data-ttu-id="88064-129">Zamknij hosta usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88064-129">Close the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="88064-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="88064-130">Example</span></span>  
 <span data-ttu-id="88064-131">Poniżej znajduje się pełny kod dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="88064-131">The following is the full code listing for this topic.</span></span>  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88064-132">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="88064-132">Compiling the Code</span></span>  
 <span data-ttu-id="88064-133">W przypadku kompilowania kodu Service.cs, odwołanie System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="88064-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88064-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88064-134">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="88064-135">Model programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="88064-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
