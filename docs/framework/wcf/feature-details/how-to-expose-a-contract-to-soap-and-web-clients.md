---
title: 'Instrukcje: ujawnianie kontraktu klientom internetowym i SOAP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: d82c5e3fc33528eadc3c404cca59a3dcf905e0e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000925"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="bdd31-102">Instrukcje: ujawnianie kontraktu klientom internetowym i SOAP</span><span class="sxs-lookup"><span data-stu-id="bdd31-102">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="bdd31-103">Domyślnie program Windows Communication Foundation (WCF) sprawia, że punkty końcowe dostępne tylko dla klientów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bdd31-103">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="bdd31-104">W [jak: Utwórz podstawowa usługa HTTP w sieci Web WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), punkt końcowy jest udostępniana klientom protokołem SOAP.</span><span class="sxs-lookup"><span data-stu-id="bdd31-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="bdd31-105">Mogą wystąpić sytuacje, kiedy chcesz udostępnić ten sam kontrakt obu kierunkach, jako punkt końcowy sieci Web, a punkt końcowy protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bdd31-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="bdd31-106">W tym temacie przedstawiono przykład sposobu wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="bdd31-106">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="bdd31-107">Aby zdefiniować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="bdd31-107">To define the service contract</span></span>

1. <span data-ttu-id="bdd31-108">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybuty, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bdd31-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="bdd31-109">Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołań operacji POST.</span><span class="sxs-lookup"><span data-stu-id="bdd31-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="bdd31-110">Można jednak określić metodę do mapowania na operację, określając "metoda =" parametru.</span><span class="sxs-lookup"><span data-stu-id="bdd31-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="bdd31-111"><xref:System.ServiceModel.Web.WebGetAttribute> nie ma "metoda =" parametr i tylko mapy GET wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="bdd31-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="bdd31-112">Implementowanie kontraktu usługi, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bdd31-112">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="bdd31-113">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="bdd31-113">To host the service</span></span>

1. <span data-ttu-id="bdd31-114">Utwórz <xref:System.ServiceModel.ServiceHost> obiektu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bdd31-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="bdd31-115">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.BasicHttpBinding> dla punktu końcowego protokołu SOAP, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bdd31-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="bdd31-116">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.WebHttpBinding> dla punktu końcowego protokołem SOAP i Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bdd31-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="bdd31-117">Wywołaj `Open()` na <xref:System.ServiceModel.ServiceHost> wystąpienia, aby otworzyć hosta usługi, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="bdd31-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="bdd31-118">Do wywołania operacji usługi mapowane na GET w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="bdd31-118">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="bdd31-119">Otwórz program Internet Explorer i wpisz "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="bdd31-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="bdd31-120">Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/`), adres względny punktu końcowego (""), operacja usługi do wywołania ("EchoWithGet") i znak zapytania, a następnie listę nazwanych parametrów rozdzielone handlowe "i" (&).</span><span class="sxs-lookup"><span data-stu-id="bdd31-120">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="bdd31-121">Do wywołania operacji usługi w punkcie końcowym sieci Web w kodzie</span><span class="sxs-lookup"><span data-stu-id="bdd31-121">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="bdd31-122">Utwórz wystąpienie obiektu <xref:System.ServiceModel.Web.WebChannelFactory%601> w ramach `using` zablokować, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdd31-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="bdd31-123">`Close()` jest wywoływana automatycznie w kanale na końcu `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="bdd31-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="bdd31-124">Utwórz kanał i wywołać usługę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdd31-124">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="bdd31-125">Do wywołania operacji usługi w punkcie końcowym protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="bdd31-125">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="bdd31-126">Utwórz wystąpienie obiektu <xref:System.ServiceModel.ChannelFactory> w ramach `using` zablokować, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdd31-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="bdd31-127">Utwórz kanał i wywołać usługę, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdd31-127">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="bdd31-128">Aby zamknąć hosta usługi</span><span class="sxs-lookup"><span data-stu-id="bdd31-128">To close the service host</span></span>

1. <span data-ttu-id="bdd31-129">Zamknij hosta usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdd31-129">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="bdd31-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdd31-130">Example</span></span>

<span data-ttu-id="bdd31-131">Oto pełny kod dla tego tematu:</span><span class="sxs-lookup"><span data-stu-id="bdd31-131">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="bdd31-132">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bdd31-132">Compiling the code</span></span>

 <span data-ttu-id="bdd31-133">Podczas kompilowania Service.cs, odwołanie System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="bdd31-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd31-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdd31-134">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="bdd31-135">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="bdd31-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)