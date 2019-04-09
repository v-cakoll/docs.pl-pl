---
title: 'Instrukcje: tworzenie podstawowego kanału informacyjnego RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 7b1ff72295332be072d7c664a546ed6e4d998ac8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073835"
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="f61d9-102">Instrukcje: tworzenie podstawowego kanału informacyjnego RSS</span><span class="sxs-lookup"><span data-stu-id="f61d9-102">How to: Create a Basic RSS Feed</span></span>
<span data-ttu-id="f61d9-103">Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia kanał.</span><span class="sxs-lookup"><span data-stu-id="f61d9-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="f61d9-104">W tym temacie omówiono sposób tworzenia usługa syndykacji, która udostępnia źródło danych RSS, źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f61d9-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="f61d9-105">Aby utworzyć usługę syndykacji podstawowe</span><span class="sxs-lookup"><span data-stu-id="f61d9-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="f61d9-106">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f61d9-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="f61d9-107">Każda operacja, która jest widoczna jako źródło danych ma zwracać <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f61d9-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f61d9-108">Wszystkie operacje usługi, które są stosowane <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu są mapowane na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="f61d9-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="f61d9-109">Aby zamapować operację na innej metody HTTP, użyj <xref:System.ServiceModel.Web.WebInvokeAttribute> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="f61d9-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="f61d9-110">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi HTTP sieci Web WCF podstawowe](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="f61d9-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="f61d9-111">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f61d9-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="f61d9-112">Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu, a następnie dodaj autora, kategoria i opis.</span><span class="sxs-lookup"><span data-stu-id="f61d9-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="f61d9-113">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f61d9-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="f61d9-114">Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> w strumieniowym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="f61d9-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="f61d9-115">Zwróć źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f61d9-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="f61d9-116">Host usługi</span><span class="sxs-lookup"><span data-stu-id="f61d9-116">To host a service</span></span>  
  
1.  <span data-ttu-id="f61d9-117">Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f61d9-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="f61d9-118">Otworzyć hosta usługi i zaczekaj, aż użytkownik naciśnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="f61d9-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="f61d9-119">Aby wywołać GetBlog() za pomocą żądania HTTP GET</span><span class="sxs-lookup"><span data-stu-id="f61d9-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="f61d9-120">Otwórz program Internet Explorer, wpisz następujący adres URL i naciśnij klawisz ENTER: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="f61d9-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span> <span data-ttu-id="f61d9-121">Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/BlogService`), adres względny punktu końcowego, a operacja usługi do wywołania.</span><span class="sxs-lookup"><span data-stu-id="f61d9-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="f61d9-122">Aby wywołać GetBlog() z kodu</span><span class="sxs-lookup"><span data-stu-id="f61d9-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="f61d9-123">Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i metody, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="f61d9-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="f61d9-124">Wywołaj statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="f61d9-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="f61d9-125">To wywołanie operacji usługi i wypełnia nową <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="f61d9-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="f61d9-126">Dostęp do obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f61d9-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="f61d9-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f61d9-127">Example</span></span>  
 <span data-ttu-id="f61d9-128">Oto pełny kod dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="f61d9-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f61d9-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f61d9-129">Compiling the Code</span></span>  
 <span data-ttu-id="f61d9-130">Podczas kompilowania w poprzednim kodzie, odwołać System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="f61d9-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61d9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f61d9-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
