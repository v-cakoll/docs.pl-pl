---
title: 'Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 17494b00259839be3beb580a516ff017ec3de50e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228409"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="6903b-102">Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="6903b-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="6903b-103">Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia kanał.</span><span class="sxs-lookup"><span data-stu-id="6903b-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="6903b-104">W tym temacie omówiono sposób tworzenia usługi syndykacji, który udostępnia kanał, za pomocą RSS 2.0 i Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="6903b-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="6903b-105">Ta usługa udostępnia jeden punkt końcowy, który może zwracać albo formacie syndykacji.</span><span class="sxs-lookup"><span data-stu-id="6903b-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="6903b-106">Dla uproszczenia usługi używane w tym przykładzie jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="6903b-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="6903b-107">W środowisku produkcyjnym usługi tego typu może być hostowana w ramach usług IIS i WAS.</span><span class="sxs-lookup"><span data-stu-id="6903b-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="6903b-108">Aby uzyskać więcej informacji o różnych technologii WCF opcji hostingu, zobacz [hostingu](../../../../docs/framework/wcf/feature-details/hosting.md).</span><span class="sxs-lookup"><span data-stu-id="6903b-108">For more information about the different WCF hosting options, see [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="6903b-109">Aby utworzyć usługę syndykacji podstawowe</span><span class="sxs-lookup"><span data-stu-id="6903b-109">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="6903b-110">Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6903b-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="6903b-111">Każda operacja, która jest widoczna jako zespolonego źródła danych zwraca <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6903b-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="6903b-112">Należy pamiętać, parametry <xref:System.ServiceModel.Web.WebGetAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6903b-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> `UriTemplate` <span data-ttu-id="6903b-113">Określa adres URL używany do wywoływania operacji tej usługi.</span><span class="sxs-lookup"><span data-stu-id="6903b-113">specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="6903b-114">Ciąg dla tego parametru zawiera literały i zmiennej w nawiasy klamrowe ({*format*}).</span><span class="sxs-lookup"><span data-stu-id="6903b-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="6903b-115">Ta zmienna odnosi się do operacji usługi `format` parametru.</span><span class="sxs-lookup"><span data-stu-id="6903b-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="6903b-116">Aby uzyskać więcej informacji, zobacz <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="6903b-116">For more information, see <xref:System.UriTemplate>.</span></span> `BodyStyle` <span data-ttu-id="6903b-117">wpływa na sposób, które tej operacji usługa wysyła i odbiera komunikaty są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="6903b-117">affects how the messages that this service operation sends and receives are written.</span></span> <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> <span data-ttu-id="6903b-118">Określa, czy dane wysyłane do i z tej operacji usługi nie są opakowane przez elementy XML zdefiniowane przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="6903b-118">specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="6903b-119">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="6903b-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6903b-120">Użyj <xref:System.ServiceModel.ServiceKnownTypeAttribute> Aby określić typy, które są zwracane przez operacje usług, w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="6903b-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2.  <span data-ttu-id="6903b-121">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="6903b-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  <span data-ttu-id="6903b-122">Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiektu, a następnie dodaj autora, kategoria i opis.</span><span class="sxs-lookup"><span data-stu-id="6903b-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  <span data-ttu-id="6903b-123">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6903b-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  <span data-ttu-id="6903b-124">Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w strumieniowym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="6903b-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  <span data-ttu-id="6903b-125">Użyj parametru formatu, aby zwrócić żądany format.</span><span class="sxs-lookup"><span data-stu-id="6903b-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="6903b-126">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="6903b-126">To host the service</span></span>  
  
1.  <span data-ttu-id="6903b-127">Tworzy obiekt <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6903b-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="6903b-128"><xref:System.ServiceModel.Web.WebServiceHost> Klasy automatycznie dodaje punkt końcowy na adres podstawowy usługi, chyba że został określony w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6903b-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="6903b-129">W tym przykładzie Brak punktów końcowych są określane tak domyślny punkt końcowy jest uwidaczniany.</span><span class="sxs-lookup"><span data-stu-id="6903b-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  <span data-ttu-id="6903b-130">Otworzyć hosta usługi, załadować źródła danych z usługi, Wyświetl źródło i czekać, aż użytkownik na naciśnięcie klawisza ENTER.</span><span class="sxs-lookup"><span data-stu-id="6903b-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="6903b-131">Aby wywołać GetBlog za pomocą żądania HTTP GET</span><span class="sxs-lookup"><span data-stu-id="6903b-131">To call GetBlog with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="6903b-132">Otwórz program Internet Explorer, wpisz następujący adres URL i naciśnij klawisz ENTER: `http://localhost:8000/BlogService/GetBlog`.</span><span class="sxs-lookup"><span data-stu-id="6903b-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="6903b-133">Adres URL zawiera adres podstawowy usługi (`http://localhost:8000/BlogService`), adres względny punktu końcowego, a operacja usługi do wywołania.</span><span class="sxs-lookup"><span data-stu-id="6903b-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="6903b-134">Aby wywołać GetBlog() z kodu</span><span class="sxs-lookup"><span data-stu-id="6903b-134">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="6903b-135">Utwórz <xref:System.Xml.XmlReader> z adresu podstawowego i metody, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="6903b-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="6903b-136">Wywołaj statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metody, przekazując <xref:System.Xml.XmlReader> właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="6903b-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="6903b-137">To wywołanie operacji usługi i wypełnia nową <xref:System.ServiceModel.Syndication.SyndicationFeed> z elementem formatującym zwrócony przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="6903b-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="6903b-138">Dostęp do obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="6903b-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="6903b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="6903b-139">Example</span></span>  
 <span data-ttu-id="6903b-140">Oto pełny kod dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="6903b-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6903b-141">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6903b-141">Compiling the Code</span></span>  
 <span data-ttu-id="6903b-142">Podczas kompilowania w poprzednim kodzie, odwołać System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="6903b-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6903b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6903b-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
