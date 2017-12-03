---
title: "Porady: udostępnianie źródło danych jako Atom i RSS"
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
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dad8fe137cfc495d1edc6936d13830861e1654e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="55c3d-102">Porady: udostępnianie źródło danych jako Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="55c3d-102">How to: Expose a Feed as Both Atom and RSS</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="55c3d-103">Służy do tworzenia usługi, który ujawnia zespolonego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="55c3d-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="55c3d-104">W tym temacie omówiono sposób tworzenia usługa syndykacji ujawniający zespolonego źródła danych przy użyciu zarówno Atom 1.0 i RSS 2.0.</span><span class="sxs-lookup"><span data-stu-id="55c3d-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="55c3d-105">Ta usługa udostępnia jeden punkt końcowy, który może zwrócić albo formacie zespolonego.</span><span class="sxs-lookup"><span data-stu-id="55c3d-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="55c3d-106">Dla uproszczenia usługę używaną w tym przykładzie jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="55c3d-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="55c3d-107">W środowisku produkcyjnym usługi tego typu może być hostowana w ramach usług IIS lub WAS.</span><span class="sxs-lookup"><span data-stu-id="55c3d-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="55c3d-108">różnych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting opcji, zobacz [hostingu](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="55c3d-108"> the different [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="55c3d-109">Aby utworzyć usługę zespolonego podstawowe</span><span class="sxs-lookup"><span data-stu-id="55c3d-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="55c3d-110">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="55c3d-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="55c3d-111">Każda operacja uwidocznioną jak zespolonego źródła danych zwraca <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="55c3d-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="55c3d-112">Należy pamiętać, parametry <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="55c3d-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="55c3d-113">`UriTemplate`Określa adres URL używany do wywołania tej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="55c3d-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="55c3d-114">Ciąg dla tego parametru zawiera literały i zmiennej w nawiasach klamrowych ({*format*}).</span><span class="sxs-lookup"><span data-stu-id="55c3d-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="55c3d-115">Ta zmienna odnosi się do operacji usługi `format` parametru.</span><span class="sxs-lookup"><span data-stu-id="55c3d-115">This variable corresponds to the service operation's `format` parameter.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="55c3d-116"> <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="55c3d-116"> <xref:System.UriTemplate>.</span></span> <span data-ttu-id="55c3d-117">`BodyStyle`wpływa na sposób tej operacji usługi wysyła i odbiera komunikaty są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="55c3d-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="55c3d-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Określa, że dane wysyłane do i z tej operacji usługi nie są opakowane w usłudze zdefiniowane infrastruktury elementów XML.</span><span class="sxs-lookup"><span data-stu-id="55c3d-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="55c3d-119"> <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="55c3d-119"> <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="55c3d-120">Użyj <xref:System.ServiceModel.ServiceKnownTypeAttribute> Aby określić typy, które są zwracane przez operacje usług w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="55c3d-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="55c3d-121">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="55c3d-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="55c3d-122">Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu i dodać autora, kategoria i opis.</span><span class="sxs-lookup"><span data-stu-id="55c3d-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="55c3d-123">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="55c3d-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="55c3d-124">Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="55c3d-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="55c3d-125">Użyj parametru formatu, aby zwrócić żądany format.</span><span class="sxs-lookup"><span data-stu-id="55c3d-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="55c3d-126">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="55c3d-126">To host the service</span></span>  
  
1.  <span data-ttu-id="55c3d-127">Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiektu.</span><span class="sxs-lookup"><span data-stu-id="55c3d-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="55c3d-128"><xref:System.ServiceModel.Web.WebServiceHost> Klasy automatycznie dodaje punkt końcowy na adres podstawowy usługi, chyba że został określony w konfiguracji lub kodu.</span><span class="sxs-lookup"><span data-stu-id="55c3d-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="55c3d-129">W tym przykładzie punkty końcowe nie są określone, domyślny punkt końcowy jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="55c3d-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="55c3d-130">Otworzyć hosta usługi, załadować źródła strumieniowego z usługi, Wyświetl źródło i poczekaj, aż użytkownikowi naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="55c3d-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="55c3d-131">Aby wywołać GetBlog z HTTP GET</span><span class="sxs-lookup"><span data-stu-id="55c3d-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="55c3d-132">Otwórz program Internet Explorer, wpisz następujący adres URL, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="55c3d-132">Open Internet Explorer, type the following URL, and press ENTER.</span></span> <span data-ttu-id="55c3d-133">http://localhost: 8000/BlogService/GetBlog</span><span class="sxs-lookup"><span data-stu-id="55c3d-133">http://localhost:8000/BlogService/GetBlog</span></span>  
  
     <span data-ttu-id="55c3d-134">Adres URL zawiera adres podstawowy usługi (http://localhost: 8000/BlogService), względny adres punktu końcowego i do wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="55c3d-134">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="55c3d-135">Aby wywołać GetBlog() z kodu</span><span class="sxs-lookup"><span data-stu-id="55c3d-135">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="55c3d-136">Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="55c3d-136">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="55c3d-137">Wywołaj statycznych <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="55c3d-137">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="55c3d-138">To wywołanie operacji usługi i wypełnia nowy <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="55c3d-138">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="55c3d-139">Dostęp do źródła strumieniowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="55c3d-139">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="55c3d-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="55c3d-140">Example</span></span>  
 <span data-ttu-id="55c3d-141">Poniżej znajduje się pełna listy w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="55c3d-141">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55c3d-142">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="55c3d-142">Compiling the Code</span></span>  
 <span data-ttu-id="55c3d-143">W przypadku kompilowania kodu poprzedni kod, odniesienia System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="55c3d-143">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c3d-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55c3d-144">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
