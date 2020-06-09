---
title: 'Instrukcje: Tworzenie podstawowego źródła danych Atom'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 0317e7b42f589b31f5c77b89d26cb46815f13054
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599051"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="d65d9-102">Instrukcje: Tworzenie podstawowego źródła danych Atom</span><span class="sxs-lookup"><span data-stu-id="d65d9-102">How to: Create a Basic Atom Feed</span></span>
<span data-ttu-id="d65d9-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia zespolone źródło danych.</span><span class="sxs-lookup"><span data-stu-id="d65d9-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="d65d9-104">W tym temacie omówiono sposób tworzenia usługi zespolonej, która uwidacznia strumieniowe źródło danych Atom.</span><span class="sxs-lookup"><span data-stu-id="d65d9-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="d65d9-105">Aby utworzyć podstawową usługę zespalania</span><span class="sxs-lookup"><span data-stu-id="d65d9-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="d65d9-106">Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego <xref:System.ServiceModel.Web.WebGetAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="d65d9-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="d65d9-107">Każda operacja, która jest udostępniana jako zespolone źródło danych, powinna zwracać <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> obiekt.</span><span class="sxs-lookup"><span data-stu-id="d65d9-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="d65d9-108">Wszystkie operacje usługi, które mają zastosowanie, <xref:System.ServiceModel.Web.WebGetAttribute> są mapowane na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="d65d9-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="d65d9-109">Aby zmapować operację na inną metodę HTTP, użyj <xref:System.ServiceModel.Web.WebInvokeAttribute> zamiast niego.</span><span class="sxs-lookup"><span data-stu-id="d65d9-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="d65d9-110">Aby uzyskać więcej informacji, zobacz [How to: Create a Basic Internet http Web Service](how-to-create-a-basic-wcf-web-http-service.md).</span><span class="sxs-lookup"><span data-stu-id="d65d9-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="d65d9-111">Zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="d65d9-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="d65d9-112">Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiekt i Dodaj autora, kategorię i opis.</span><span class="sxs-lookup"><span data-stu-id="d65d9-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="d65d9-113">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d65d9-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="d65d9-114">Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> obiekty do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d65d9-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="d65d9-115">Zwróć źródło danych.</span><span class="sxs-lookup"><span data-stu-id="d65d9-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="d65d9-116">Aby hostować usługę</span><span class="sxs-lookup"><span data-stu-id="d65d9-116">To host the service</span></span>  
  
1. <span data-ttu-id="d65d9-117">Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiekt.</span><span class="sxs-lookup"><span data-stu-id="d65d9-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="d65d9-118">Otwórz hosta usługi, Załaduj źródło danych z usługi, Wyświetl źródło i poczekaj na naciśnięcie klawisza ENTER przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d65d9-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="d65d9-119">Aby wywołać metodę getblog () przy użyciu protokołu HTTP GET</span><span class="sxs-lookup"><span data-stu-id="d65d9-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="d65d9-120">Otwórz program Internet Explorer, wpisz następujący adres URL i naciśnij klawisz ENTER:`http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="d65d9-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="d65d9-121">Adres URL zawiera adres podstawowy usługi ( `http://localhost:8000/BlogService` ), adres względny punktu końcowego i operację usługi do wywołania.</span><span class="sxs-lookup"><span data-stu-id="d65d9-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="d65d9-122">Aby wywołać metodę getblog () z kodu</span><span class="sxs-lookup"><span data-stu-id="d65d9-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="d65d9-123">Utwórz <xref:System.Xml.XmlReader> z adresem podstawowym i metodą, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="d65d9-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="d65d9-124">Wywołaj metodę statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> , przekazując w <xref:System.Xml.XmlReader> właśnie utworzony sposób.</span><span class="sxs-lookup"><span data-stu-id="d65d9-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="d65d9-125">Spowoduje to wywołanie operacji usługi i wypełnienie nowej <xref:System.ServiceModel.Syndication.SyndicationFeed> z programem formatującego zwróconym przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="d65d9-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="d65d9-126">Dostęp do obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d65d9-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="d65d9-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d65d9-127">Example</span></span>  
 <span data-ttu-id="d65d9-128">Poniżej znajduje się pełna lista kodów dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="d65d9-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d65d9-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d65d9-129">Compiling the Code</span></span>  
 <span data-ttu-id="d65d9-130">Podczas kompilowania powyższego kodu odwołuje się do System. ServiceModel. dll i system. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="d65d9-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d65d9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d65d9-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
