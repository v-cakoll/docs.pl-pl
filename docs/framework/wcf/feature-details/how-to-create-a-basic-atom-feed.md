---
title: 'Instrukcje: tworzenie podstawowego źródła danych Atom'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 82095f397195fbf333bab8d043da18114e2a5dba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968472"
---
# <a name="how-to-create-a-basic-atom-feed"></a><span data-ttu-id="c50a1-102">Instrukcje: tworzenie podstawowego źródła danych Atom</span><span class="sxs-lookup"><span data-stu-id="c50a1-102">How to: Create a Basic Atom Feed</span></span>
<span data-ttu-id="c50a1-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia zespolone źródło danych.</span><span class="sxs-lookup"><span data-stu-id="c50a1-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="c50a1-104">W tym temacie omówiono sposób tworzenia usługi zespolonej, która uwidacznia strumieniowe źródło danych Atom.</span><span class="sxs-lookup"><span data-stu-id="c50a1-104">This topic discusses how to create a syndication service that exposes an Atom syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="c50a1-105">Aby utworzyć podstawową usługę zespalania</span><span class="sxs-lookup"><span data-stu-id="c50a1-105">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="c50a1-106">Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego <xref:System.ServiceModel.Web.WebGetAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="c50a1-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="c50a1-107">Każda operacja, która jest udostępniana jako zespolone źródło danych <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> , powinna zwracać obiekt.</span><span class="sxs-lookup"><span data-stu-id="c50a1-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> object.</span></span>  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="c50a1-108">Wszystkie operacje usługi, które mają <xref:System.ServiceModel.Web.WebGetAttribute> zastosowanie, są mapowane na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="c50a1-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> are mapped to HTTP GET requests.</span></span> <span data-ttu-id="c50a1-109">Aby zmapować operację na inną metodę http, użyj <xref:System.ServiceModel.Web.WebInvokeAttribute> zamiast niego.</span><span class="sxs-lookup"><span data-stu-id="c50a1-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="c50a1-110">Aby uzyskać więcej informacji, zobacz [jak: Utwórz podstawową usługę](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)http sieci Web w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="c50a1-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2. <span data-ttu-id="c50a1-111">Zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="c50a1-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. <span data-ttu-id="c50a1-112"><xref:System.ServiceModel.Syndication.SyndicationFeed> Utwórz obiekt i Dodaj autora, kategorię i opis.</span><span class="sxs-lookup"><span data-stu-id="c50a1-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. <span data-ttu-id="c50a1-113">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c50a1-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <span data-ttu-id="c50a1-114"><xref:System.ServiceModel.Syndication.SyndicationItem> Dodaj obiekty do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c50a1-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. <span data-ttu-id="c50a1-115">Zwróć źródło danych.</span><span class="sxs-lookup"><span data-stu-id="c50a1-115">Return the feed.</span></span>  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="c50a1-116">Aby hostować usługę</span><span class="sxs-lookup"><span data-stu-id="c50a1-116">To host the service</span></span>  
  
1. <span data-ttu-id="c50a1-117">Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c50a1-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. <span data-ttu-id="c50a1-118">Otwórz hosta usługi, Załaduj źródło danych z usługi, Wyświetl źródło i poczekaj na naciśnięcie klawisza ENTER przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c50a1-118">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="c50a1-119">Aby wywołać metodę getblog () przy użyciu protokołu HTTP GET</span><span class="sxs-lookup"><span data-stu-id="c50a1-119">To call GetBlog() with an HTTP GET</span></span>  
  
1. <span data-ttu-id="c50a1-120">Otwórz program Internet Explorer, wpisz następujący adres URL i naciśnij klawisz ENTER:`http://localhost:8000/BlogService/GetBlog`</span><span class="sxs-lookup"><span data-stu-id="c50a1-120">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`</span></span>  
  
     <span data-ttu-id="c50a1-121">Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/BlogService`), adres względny punktu końcowego i operację usługi do wywołania.</span><span class="sxs-lookup"><span data-stu-id="c50a1-121">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="c50a1-122">Aby wywołać metodę getblog () z kodu</span><span class="sxs-lookup"><span data-stu-id="c50a1-122">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="c50a1-123"><xref:System.Xml.XmlReader> Utwórz z adresem podstawowym i metodą, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="c50a1-123">Create a <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="c50a1-124">Wywołaj metodę <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> statyczną, przekazując <xref:System.Xml.XmlReader> w właśnie utworzony sposób.</span><span class="sxs-lookup"><span data-stu-id="c50a1-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="c50a1-125">Spowoduje to wywołanie operacji usługi i wypełnienie nowej <xref:System.ServiceModel.Syndication.SyndicationFeed> z programem formatującego zwróconym przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="c50a1-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="c50a1-126">Dostęp do obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c50a1-126">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="c50a1-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="c50a1-127">Example</span></span>  
 <span data-ttu-id="c50a1-128">Poniżej znajduje się pełna lista kodów dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="c50a1-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c50a1-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c50a1-129">Compiling the Code</span></span>  
 <span data-ttu-id="c50a1-130">Podczas kompilowania powyższego kodu odwołuje się do System. ServiceModel. dll i system. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="c50a1-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c50a1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c50a1-131">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
