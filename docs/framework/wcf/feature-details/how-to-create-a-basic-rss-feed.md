---
title: "Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS"
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
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54b9932e081ab5f35b3c15c9e7d4025dfbb3703b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="047fe-102">Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS</span><span class="sxs-lookup"><span data-stu-id="047fe-102">How to: Create a Basic RSS Feed</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="047fe-103">Służy do tworzenia usługi, który ujawnia zespolonego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="047fe-103"> allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="047fe-104">W tym temacie omówiono sposób tworzenia usługa syndykacji ujawniający źródła zespolonego RSS.</span><span class="sxs-lookup"><span data-stu-id="047fe-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="047fe-105">Aby utworzyć usługę zespolonego podstawowe</span><span class="sxs-lookup"><span data-stu-id="047fe-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="047fe-106">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="047fe-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="047fe-107">Każda operacja uwidocznioną jak zespolonego źródła powinna zwrócić <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="047fe-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="047fe-108">Wszystkie operacje usługi, które są stosowane <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu są mapowane na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="047fe-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="047fe-109">Aby mapować operację na innej metody HTTP, należy użyć <xref:System.ServiceModel.Web.WebInvokeAttribute> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="047fe-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="047fe-110">[Porady: Tworzenie usługi HTTP sieci Web WCF podstawowe](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="047fe-110"> [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="047fe-111">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="047fe-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="047fe-112">Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu i dodać autora, kategoria i opis.</span><span class="sxs-lookup"><span data-stu-id="047fe-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="047fe-113">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="047fe-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="047fe-114">Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="047fe-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="047fe-115">Zwróć kanału informacyjnego.</span><span class="sxs-lookup"><span data-stu-id="047fe-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="047fe-116">Do hosta usługi</span><span class="sxs-lookup"><span data-stu-id="047fe-116">To host a service</span></span>  
  
1.  <span data-ttu-id="047fe-117">Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiektu.</span><span class="sxs-lookup"><span data-stu-id="047fe-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="047fe-118">Otworzyć hosta usługi i poczekaj, aż użytkownik naciśnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="047fe-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="047fe-119">Aby wywołać GetBlog() z HTTP GET</span><span class="sxs-lookup"><span data-stu-id="047fe-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="047fe-120">Otwórz program Internet Explorer, wpisz następujący adres URL, a następnie naciśnij klawisz ENTER: http://localhost: 8000/BlogService/GetBlog.</span><span class="sxs-lookup"><span data-stu-id="047fe-120">Open Internet Explorer, type the following URL, and press ENTER: http://localhost:8000/BlogService/GetBlog.</span></span> <span data-ttu-id="047fe-121">Adres URL zawiera adres podstawowy usługi (http://localhost: 8000/BlogService), względny adres punktu końcowego i do wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="047fe-121">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="047fe-122">Aby wywołać GetBlog() z kodu</span><span class="sxs-lookup"><span data-stu-id="047fe-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="047fe-123">Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="047fe-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="047fe-124">Wywołaj statycznych <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="047fe-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="047fe-125">To wywołanie operacji usługi i wypełnia nowy <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="047fe-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="047fe-126">Dostęp do źródła strumieniowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="047fe-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="047fe-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="047fe-127">Example</span></span>  
 <span data-ttu-id="047fe-128">Poniżej znajduje się pełna listy w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="047fe-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="047fe-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="047fe-129">Compiling the Code</span></span>  
 <span data-ttu-id="047fe-130">W przypadku kompilowania kodu poprzedni kod, odniesienia System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="047fe-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047fe-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="047fe-131">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
