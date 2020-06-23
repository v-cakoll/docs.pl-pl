---
title: 'Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF'
description: Dowiedz się, jak utworzyć usługę, która uwidacznia punkt końcowy sieci Web w programie WCF. Punkty końcowe sieci Web wysyłają dane przy użyciu kodu XML lub JSON. Brak koperty protokołu SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247107"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="566df-105">Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="566df-105">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="566df-106">Windows Communication Foundation (WCF) umożliwia tworzenie usługi, która uwidacznia punkt końcowy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="566df-106">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="566df-107">Punkty końcowe sieci Web wysyłają dane w formacie XML lub JSON, ale nie ma koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="566df-107">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="566df-108">W tym temacie pokazano, jak uwidocznić taki punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="566df-108">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="566df-109">Jedynym sposobem zabezpieczenia punktu końcowego sieci Web jest udostępnienie go za pośrednictwem protokołu HTTPS przy użyciu zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="566df-109">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="566df-110">W przypadku korzystania z zabezpieczeń opartych na komunikatach informacje o zabezpieczeniach są zwykle umieszczane w nagłówkach protokołu SOAP, a ponieważ komunikaty wysyłane do punktów końcowych innych niż SOAP nie zawierają koperty protokołu SOAP, nie można umieścić informacji o zabezpieczeniach i należy polegać na zabezpieczeniach transportu.</span><span class="sxs-lookup"><span data-stu-id="566df-110">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="566df-111">Aby utworzyć punkt końcowy sieci Web</span><span class="sxs-lookup"><span data-stu-id="566df-111">To create a Web endpoint</span></span>

1. <span data-ttu-id="566df-112">Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego za pomocą <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="566df-112">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="566df-113">Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania do operacji.</span><span class="sxs-lookup"><span data-stu-id="566df-113">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="566df-114">Można jednak określić metodę HTTP (na przykład, nagłówek, PUT lub DELETE) do mapowania do operacji przez określenie parametru "Metoda =".</span><span class="sxs-lookup"><span data-stu-id="566df-114">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="566df-115"><xref:System.ServiceModel.Web.WebGetAttribute>nie ma parametru "Method =" i tylko mapuje wywołania GET do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="566df-115"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="566df-116">Zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="566df-116">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="566df-117">Aby hostować usługę</span><span class="sxs-lookup"><span data-stu-id="566df-117">To host the service</span></span>

1. <span data-ttu-id="566df-118">Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiekt.</span><span class="sxs-lookup"><span data-stu-id="566df-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="566df-119">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> przy użyciu <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="566df-119">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="566df-120">Jeśli nie dodasz punktu końcowego, program <xref:System.ServiceModel.Web.WebServiceHost> automatycznie utworzy domyślny punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="566df-120">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="566df-121"><xref:System.ServiceModel.Web.WebServiceHost>Ponadto dodaje <xref:System.ServiceModel.Description.WebHttpBehavior> i wyłącza stronę pomocy http i funkcję pobierania Web Services Description Language (WSDL), dzięki czemu punkt końcowy metadanych nie zakłóca domyślnego punktu końcowego http.</span><span class="sxs-lookup"><span data-stu-id="566df-121"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="566df-122">Dodanie punktu końcowego innego niż SOAP o adresie URL "" powoduje nieoczekiwane zachowanie, gdy podjęto próbę wywołania operacji w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="566df-122">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="566df-123">Przyczyną tego jest identyfikator URI nasłuchiwania punktu końcowego, który jest taki sam jak identyfikator URI strony pomocy (strona wyświetlana po przejściu na adres podstawowy usługi WCF).</span><span class="sxs-lookup"><span data-stu-id="566df-123">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="566df-124">Można wykonać jedną z następujących czynności, aby zapobiec takiej sytuacji:</span><span class="sxs-lookup"><span data-stu-id="566df-124">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="566df-125">Zawsze należy określić niepusty identyfikator URI dla punktu końcowego innego niż SOAP.</span><span class="sxs-lookup"><span data-stu-id="566df-125">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="566df-126">Wyłącz stronę pomocy.</span><span class="sxs-lookup"><span data-stu-id="566df-126">Turn off the help page.</span></span> <span data-ttu-id="566df-127">Można to zrobić przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="566df-127">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="566df-128">Otwórz hosta usługi i poczekaj, aż użytkownik naciśnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="566df-128">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="566df-129">Ten przykład pokazuje, jak hostować usługę w stylu sieci Web za pomocą aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="566df-129">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="566df-130">Możesz również hostować taką usługę w ramach usług IIS.</span><span class="sxs-lookup"><span data-stu-id="566df-130">You can also host such a service within IIS.</span></span> <span data-ttu-id="566df-131">W tym celu należy określić <xref:System.ServiceModel.Activation.WebServiceHostFactory> klasę w pliku SVC, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="566df-131">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="566df-132">Aby wywołać operacje usługi mapowane do pobrania w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="566df-132">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="566df-133">Otwórz program Internet Explorer i wpisz " `http://localhost:8000/EchoWithGet?s=Hello, world!` " i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="566df-133">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="566df-134">Adres URL zawiera adres podstawowy usługi ( `http://localhost:8000/` ), adres względny punktu końcowego (""), operację usługi do wywołania ("EchoWithGet") i znak zapytania oraz listę nazwanych parametrów oddzielonych znakiem handlowego "i" (&).</span><span class="sxs-lookup"><span data-stu-id="566df-134">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="566df-135">Aby wywołać operacje usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="566df-135">To call service operations in code</span></span>

1. <span data-ttu-id="566df-136">Utwórz wystąpienie <xref:System.ServiceModel.ChannelFactory%601> w `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="566df-136">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="566df-137">Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego <xref:System.ServiceModel.ChannelFactory%601> wywołań.</span><span class="sxs-lookup"><span data-stu-id="566df-137">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="566df-138">Utwórz kanał i Wywołaj usługę.</span><span class="sxs-lookup"><span data-stu-id="566df-138">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="566df-139">Zamknij okno <xref:System.ServiceModel.Web.WebServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="566df-139">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="566df-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="566df-140">Example</span></span>

<span data-ttu-id="566df-141">Poniżej znajduje się pełna lista kodów dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="566df-141">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="566df-142">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="566df-142">Compiling the code</span></span>

<span data-ttu-id="566df-143">Podczas kompilowania System.ServiceModel.dll odwołania do Service.cs i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="566df-143">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="566df-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="566df-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="566df-145">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="566df-145">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
