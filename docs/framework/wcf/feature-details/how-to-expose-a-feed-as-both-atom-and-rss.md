---
title: 'Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: e4ce1fa7b494c2317a1bddc57ee6b150c84b9a96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593149"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="90d10-102">Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="90d10-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="90d10-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia zespolone źródło danych.</span><span class="sxs-lookup"><span data-stu-id="90d10-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="90d10-104">W tym temacie omówiono sposób tworzenia usługi zespolonej, która uwidacznia zespolone źródło danych za pomocą Atom 1,0 i RSS 2,0.</span><span class="sxs-lookup"><span data-stu-id="90d10-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="90d10-105">Ta usługa ujawnia jeden punkt końcowy, który może zwracać format zespolony.</span><span class="sxs-lookup"><span data-stu-id="90d10-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="90d10-106">Dla uproszczenia Usługa używana w tym przykładzie jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="90d10-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="90d10-107">W środowisku produkcyjnym usługi tego typu byłyby hostowane w usługach IIS lub WAS.</span><span class="sxs-lookup"><span data-stu-id="90d10-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="90d10-108">Aby uzyskać więcej informacji na temat różnych opcji hostingu WCF, zobacz [hosting](hosting.md).</span><span class="sxs-lookup"><span data-stu-id="90d10-108">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="90d10-109">Aby utworzyć podstawową usługę zespalania</span><span class="sxs-lookup"><span data-stu-id="90d10-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="90d10-110">Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego <xref:System.ServiceModel.Web.WebGetAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="90d10-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="90d10-111">Każda operacja, która jest udostępniana jako zespolone źródło danych, zwraca <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiekt.</span><span class="sxs-lookup"><span data-stu-id="90d10-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="90d10-112">Zwróć uwagę na parametry <xref:System.ServiceModel.Web.WebGetAttribute> .</span><span class="sxs-lookup"><span data-stu-id="90d10-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="90d10-113">`UriTemplate`Określa adres URL służący do wywoływania tej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="90d10-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="90d10-114">Ciąg dla tego parametru zawiera literały i zmienną w nawiasach klamrowych ({*Format*}).</span><span class="sxs-lookup"><span data-stu-id="90d10-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="90d10-115">Ta zmienna odpowiada `format` parametrowi operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="90d10-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="90d10-116">Aby uzyskać więcej informacji, zobacz <xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="90d10-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="90d10-117">`BodyStyle`wpływa na to, w jaki sposób wiadomości wysyłane i odbierane przez tę operację usługi są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="90d10-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="90d10-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Określa, że dane wysyłane do i z tej operacji usługi nie są opakowane przez zdefiniowane przez infrastrukturę elementy XML.</span><span class="sxs-lookup"><span data-stu-id="90d10-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="90d10-119">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span><span class="sxs-lookup"><span data-stu-id="90d10-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="90d10-120">Użyj, <xref:System.ServiceModel.ServiceKnownTypeAttribute> Aby określić typy, które są zwracane przez operacje usługi w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="90d10-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="90d10-121">Zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="90d10-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="90d10-122">Utwórz <xref:System.ServiceModel.Syndication.SyndicationFeed> obiekt i Dodaj autora, kategorię i opis.</span><span class="sxs-lookup"><span data-stu-id="90d10-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="90d10-123">Utwórz kilka <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="90d10-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="90d10-124">Dodaj <xref:System.ServiceModel.Syndication.SyndicationItem> obiekty do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="90d10-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="90d10-125">Użyj parametru format, aby zwrócić żądany format.</span><span class="sxs-lookup"><span data-stu-id="90d10-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="90d10-126">Aby hostować usługę</span><span class="sxs-lookup"><span data-stu-id="90d10-126">To host the service</span></span>  
  
1. <span data-ttu-id="90d10-127">Utwórz <xref:System.ServiceModel.Web.WebServiceHost> obiekt.</span><span class="sxs-lookup"><span data-stu-id="90d10-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="90d10-128"><xref:System.ServiceModel.Web.WebServiceHost>Klasa automatycznie dodaje punkt końcowy pod adresem podstawowym usługi, chyba że jest określony w kodzie lub konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="90d10-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="90d10-129">W tym przykładzie nie określono żadnych punktów końcowych, więc domyślny punkt końcowy jest ujawniany.</span><span class="sxs-lookup"><span data-stu-id="90d10-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="90d10-130">Otwórz hosta usługi, Załaduj źródło danych z usługi, Wyświetl źródło i poczekaj na naciśnięcie klawisza ENTER przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="90d10-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="90d10-131">Aby wywołać metodę getblog przy użyciu protokołu HTTP GET</span><span class="sxs-lookup"><span data-stu-id="90d10-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="90d10-132">Otwórz program Internet Explorer, wpisz następujący adres URL, a następnie naciśnij klawisz ENTER: `http://localhost:8000/BlogService/GetBlog` .</span><span class="sxs-lookup"><span data-stu-id="90d10-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="90d10-133">Adres URL zawiera adres podstawowy usługi ( `http://localhost:8000/BlogService` ), adres względny punktu końcowego i operację usługi do wywołania.</span><span class="sxs-lookup"><span data-stu-id="90d10-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="90d10-134">Aby wywołać metodę getblog () z kodu</span><span class="sxs-lookup"><span data-stu-id="90d10-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="90d10-135">Utwórz <xref:System.Xml.XmlReader> z adresem podstawowym i metodą, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="90d10-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="90d10-136">Wywołaj metodę statyczną <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> , przekazując w <xref:System.Xml.XmlReader> właśnie utworzony sposób.</span><span class="sxs-lookup"><span data-stu-id="90d10-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="90d10-137">Spowoduje to wywołanie operacji usługi i wypełnienie nowej <xref:System.ServiceModel.Syndication.SyndicationFeed> z programem formatującego zwróconym przez operację usługi.</span><span class="sxs-lookup"><span data-stu-id="90d10-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="90d10-138">Dostęp do obiektu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="90d10-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="90d10-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="90d10-139">Example</span></span>  
 <span data-ttu-id="90d10-140">Poniżej znajduje się pełna lista kodów dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="90d10-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="90d10-141">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="90d10-141">Compiling the Code</span></span>  
 <span data-ttu-id="90d10-142">Podczas kompilowania powyższego kodu odwołuje się do System. ServiceModel. dll i system. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="90d10-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90d10-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90d10-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
