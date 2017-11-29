---
title: "Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF"
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
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8352c7761447322d1ddf8381be145e38d6b7df8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="7921e-102">Instrukcje: Tworzenie podstawowej, opartej na protokole HTTP usługi sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="7921e-102">How to: Create a Basic WCF Web HTTP Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7921e-103">Służy do tworzenia usługi, która udostępnia punkt końcowy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7921e-103"> allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="7921e-104">Punktów końcowych sieci Web wysyłać dane XML lub JSON, nie istnieje żadne koperty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7921e-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="7921e-105">W tym temacie przedstawiono sposób ujawniać punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="7921e-105">This topic demonstrates how to expose such an endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7921e-106">Jedynym sposobem, aby zabezpieczyć punkt końcowy sieci Web jest je ujawnić za pośrednictwem protokołu HTTPS, za pomocą zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="7921e-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="7921e-107">Podczas korzystania z zabezpieczeń wiadomości, informacje o zabezpieczeniach zazwyczaj znajduje się w nagłówkach protokołu SOAP i dlatego komunikaty wysyłane do punktów końcowych SOAP nie zawiera żadnych koperty protokołu SOAP, nie nigdzie nie można umieścić informacji o zabezpieczeniach i konieczne jest zastosowanie zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="7921e-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>  
  
### <a name="to-create-a-web-endpoint"></a><span data-ttu-id="7921e-108">Aby utworzyć punkt końcowy sieci Web</span><span class="sxs-lookup"><span data-stu-id="7921e-108">To create a Web endpoint</span></span>  
  
1.  <span data-ttu-id="7921e-109">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> i <xref:System.ServiceModel.Web.WebGetAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7921e-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="7921e-110">Domyślnie <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje wywołania operacji POST.</span><span class="sxs-lookup"><span data-stu-id="7921e-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="7921e-111">Można jednak określić metodę HTTP (na przykład HEAD, PUT lub usuń) do mapowania na operację, określając "metody =" parametru.</span><span class="sxs-lookup"><span data-stu-id="7921e-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="7921e-112"><xref:System.ServiceModel.Web.WebGetAttribute>nie ma "metody =" parametru i map tylko GET wywołania do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7921e-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="7921e-113">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7921e-113">Implement the service contract.</span></span>  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="7921e-114">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="7921e-114">To host the service</span></span>  
  
1.  <span data-ttu-id="7921e-115">Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7921e-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  <span data-ttu-id="7921e-116">Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> z <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="7921e-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="7921e-117">Jeśli nie zostanie dodany punkt końcowy <xref:System.ServiceModel.Web.WebServiceHost> automatycznie tworzy domyślny punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="7921e-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="7921e-118"><xref:System.ServiceModel.Web.WebServiceHost>dodaje również <xref:System.ServiceModel.Description.WebHttpBehavior> i wyłącza strona pomocy HTTP oraz funkcje GET Web Services Description Language (WSDL), aby punkt końcowy metadanych nie zakłóca domyślny punkt końcowy HTTP.</span><span class="sxs-lookup"><span data-stu-id="7921e-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>  
    >   
    >  <span data-ttu-id="7921e-119">Dodawanie punktu końcowego z systemem innym niż SOAP z adresu URL "" powoduje, że nieoczekiwanego zachowania podczas próby wywołania operacji w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7921e-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="7921e-120">Przyczyną tego jest nasłuchiwania URI punktu końcowego jest taki sam jak identyfikator URI strony pomocy (strona, która jest wyświetlana podczas przeglądania adres bazowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi).</span><span class="sxs-lookup"><span data-stu-id="7921e-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service).</span></span>  
  
     <span data-ttu-id="7921e-121">Możesz wybrać jedną z następujących czynności, aby zapobiec to:</span><span class="sxs-lookup"><span data-stu-id="7921e-121">You can do one of the following actions to prevent this from happening:</span></span>  
  
    -   <span data-ttu-id="7921e-122">Zawsze należy określić niepustą identyfikatora URI dla punktu końcowego z systemem innym niż SOAP.</span><span class="sxs-lookup"><span data-stu-id="7921e-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>  
  
    -   <span data-ttu-id="7921e-123">Wyłącz strony pomocy.</span><span class="sxs-lookup"><span data-stu-id="7921e-123">Turn off the help page.</span></span> <span data-ttu-id="7921e-124">Można to zrobić z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="7921e-124">This can be done with the following code.</span></span>  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  <span data-ttu-id="7921e-125">Otworzyć hosta usługi i poczekaj, aż użytkownik naciśnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7921e-125">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     <span data-ttu-id="7921e-126">W tym przykładzie pokazano, jak udostępniać usługi stylu sieci Web za pomocą aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="7921e-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="7921e-127">Może również obsługiwać usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="7921e-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="7921e-128">Aby to zrobić, należy określić <xref:System.ServiceModel.Activation.WebServiceHostFactory> klasy w pliku SVC, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="7921e-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="7921e-129">Do wywołania operacji usługi mapowane na GET w programie Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="7921e-129">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="7921e-130">Otwórz program Internet Explorer i wpisz "`http://localhost:8000/EchoWithGet?s=Hello, world!`" i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7921e-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="7921e-131">Adres URL zawiera adres podstawowy usługi ("http://localhost: 8000 /"), względny adres punktu końcowego (""), usługi operację wywołania ("EchoWithGet") i znak zapytania następuje lista parametrów nazwanych oddzielonymi znakiem handlowego "i" (&).</span><span class="sxs-lookup"><span data-stu-id="7921e-131">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-in-code"></a><span data-ttu-id="7921e-132">Do wywołania operacji usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="7921e-132">To call service operations in code</span></span>  
  
1.  <span data-ttu-id="7921e-133">Utwórz wystąpienie <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` w `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="7921e-133">Create an instance of <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` within a `using` block.</span></span>  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  <span data-ttu-id="7921e-134">Dodaj <xref:System.ServiceModel.Description.WebHttpBehavior> do punktu końcowego <xref:System.ServiceModel.ChannelFactory> wywołania.</span><span class="sxs-lookup"><span data-stu-id="7921e-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory> calls.</span></span>  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  <span data-ttu-id="7921e-135">Tworzenie kanału i wywołania tej usługi.</span><span class="sxs-lookup"><span data-stu-id="7921e-135">Create the channel and call the service.</span></span>  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  <span data-ttu-id="7921e-136">Zamknij <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7921e-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="7921e-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="7921e-137">Example</span></span>  
 <span data-ttu-id="7921e-138">Poniżej znajduje się pełna listy w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7921e-138">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7921e-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7921e-139">Compiling the Code</span></span>  
 <span data-ttu-id="7921e-140">W przypadku kompilowania kodu odwołanie Service.cs System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="7921e-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7921e-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7921e-141">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="7921e-142">Model programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="7921e-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
