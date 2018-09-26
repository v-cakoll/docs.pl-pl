---
title: 'Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 5cebdf0bae937d84ec23ed97a5d2feca24fff473
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084189"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="56e26-102">Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="56e26-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="56e26-103">Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia obsługą ASP.NET AJAX punktu końcowego, który może zostać wywołana z języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="56e26-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="56e26-104">Opisano podstawowe procedury dotyczące tworzenia takich usług w [jak: Użyj konfiguracji, aby dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) i [porady: Dodawanie platformy ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="56e26-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="56e26-105">ASP.NET AJAX obsługuje operacje, które za pomocą usług zleceń HTTP POST i HTTP GET, POST protokołu HTTP, domyślna.</span><span class="sxs-lookup"><span data-stu-id="56e26-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="56e26-106">Podczas tworzenia operacją, która ma żadnych efektów ubocznych i zwraca dane, które nigdy lub rzadko zmieniają, użyj HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="56e26-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="56e26-107">Wyniki operacji GET mogą być buforowane, co oznacza, że wiele wywołań do tej samej operacji może spowodować tylko jedno żądanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="56e26-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="56e26-108">Buforowanie odbywa się przez architekturę WCF, ale może odbywać się na dowolnym poziomie (w przeglądarce użytkownika, na serwerze proxy i innych poziomów.) Buforowanie jest korzystne, czy chcesz zwiększyć wydajność usługi, ale nie można zaakceptować, jeśli dane zmieniają się często, czy operacja wykonuje jakąś akcję.</span><span class="sxs-lookup"><span data-stu-id="56e26-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="56e26-109">Na przykład w przypadku projektowania usługi do zarządzania użytkownika Biblioteka utworów muzycznych, operacja, która wyszukuje wykonawcy, w oparciu o albumu tytuł korzyści z używania GET, ale operacja, która albumu są dodawane do kolekcji osobistych użytkownika należy użyć POST.</span><span class="sxs-lookup"><span data-stu-id="56e26-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="56e26-110">Aby kontrolować okres istnienia pamięci podręcznej, należy użyć <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu.</span><span class="sxs-lookup"><span data-stu-id="56e26-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="56e26-111">Na przykład podczas projektowania usługi, która zwraca prognozy pogody aktualizowane co godzinę, należy użyć pobieranie, ale ograniczyć czas trwania pamięci podręcznej na godzinę lub mniej, aby uniemożliwić dostęp do starych danych w użytkownicy usługi.</span><span class="sxs-lookup"><span data-stu-id="56e26-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="56e26-112">Korzystając z usługi ze strony ASP.NET AJAX, które korzystają z kontrolki Menedżera skryptów, nie ma znaczenia, czy używa operacji GET lub POST - mechanizm Menedżera skryptów zapewnia wystawiony typu poprawnego żądania.</span><span class="sxs-lookup"><span data-stu-id="56e26-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="56e26-113">Operacje HTTP GET używają parametrów wejściowych, obsługiwane przez operacje POST, w tym typy kontraktu danych złożonych.</span><span class="sxs-lookup"><span data-stu-id="56e26-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="56e26-114">Jednak w większości przypadków zalecane jest aby uniknąć zbyt wiele parametrów lub parametry, które są zbyt złożone, w ramach operacji GET, ponieważ redukuje efektywność buforowania.</span><span class="sxs-lookup"><span data-stu-id="56e26-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="56e26-115">W tym temacie pokazano, jak wybrać między GET i POST poprzez dodanie <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty do odpowiednich operacji w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="56e26-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="56e26-116">Pozostałe kroki (w celu zaimplementowania, konfigurowania i obsługi usługi), które są wymagane, aby uzyskać usługa jest uruchomiona są podobne do tych używanych przez dowolną usługę środowiska ASP.NET AJAX w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="56e26-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="56e26-117">Operacja oznaczona za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> zawsze używa żądanie GET.</span><span class="sxs-lookup"><span data-stu-id="56e26-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="56e26-118">Operacja oznaczona za pomocą <xref:System.ServiceModel.Web.WebInvokeAttribute>, lub oznaczona za pomocą dowolnego z tych argumentów, używa żądania POST.</span><span class="sxs-lookup"><span data-stu-id="56e26-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="56e26-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> Umożliwia korzystanie z innych poleceń HTTP, innymi niż GET i POST (na przykład PUT i DELETE) za pośrednictwem <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="56e26-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="56e26-120">Tych poleceń nie są obsługiwane przez program ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="56e26-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="56e26-121">Jeśli zamierzasz korzystać z usługi strony ASP.NET, za pomocą kontrolki Menedżera skryptów, nie używaj <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="56e26-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="56e26-122">Aby uzyskać przykład pracy przełączania GET, zobacz [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="56e26-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="56e26-123">Dla przykładu korzystającego z wpisu, zobacz [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="56e26-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="56e26-124">Tworzenie usługi WCF, reaguje na HTTP GET lub POST protokołu HTTP żądania</span><span class="sxs-lookup"><span data-stu-id="56e26-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="56e26-125">Zdefiniuj podstawowego kontraktu usługi WCF z interfejsem oznaczone <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56e26-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="56e26-126">Oznaczania każdej operacji za pomocą <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="56e26-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="56e26-127">Dodaj <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby określić, że operacja powinna odpowiadać na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="56e26-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="56e26-128">Można również dodać <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu jawnie określić POST protokołu HTTP lub określono atrybut, którego wartość domyślna to POST protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="56e26-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="56e26-129">Implementowanie `IMusicService` kontraktu usługi o `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="56e26-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. <span data-ttu-id="56e26-130">Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56e26-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="56e26-131">Edytuj ten plik, dodając odpowiednie [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="56e26-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="56e26-132">Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować punktu końcowego ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="56e26-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="56e26-133">Do wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="56e26-133">To call the service</span></span>  
  
1. <span data-ttu-id="56e26-134">Operacje GET usługi bez konieczności wprowadzania kodu klienta można przetestować przy użyciu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="56e26-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="56e26-135">Na przykład, jeśli usługa jest skonfigurowana na `http://example.com/service.svc` adres, wpisując `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` do przeglądarki wywołuje usługę paska adresu i powoduje, że odpowiedź do pobrania lub wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="56e26-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="56e26-136">Za pomocą usług operacje GET w taki sam sposób jak inne usługi ASP.NET AJAX —, wprowadzając usługę kontrolować adres URL do kolekcji skryptów Menedżera skryptów AJAX programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="56e26-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="56e26-137">Aby uzyskać przykład, zobacz [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="56e26-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="56e26-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56e26-138">See Also</span></span>  
 [<span data-ttu-id="56e26-139">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="56e26-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="56e26-140">Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="56e26-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
