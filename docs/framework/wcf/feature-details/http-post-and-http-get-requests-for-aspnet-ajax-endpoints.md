---
title: 'Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: c74b1acdf3802ab680123cd9d676919fe47236e8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051587"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="bbb1d-102">Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bbb1d-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="bbb1d-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia punkt końcowy z obsługą technologii AJAX ASP.NET, który można wywołać z JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="bbb1d-104">Podstawowe procedury tworzenia takich usług zostały omówione w temacie [: używanie konfiguracji do dodawania punktu końcowego ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) i [instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez użycia konfiguracji](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="bbb1d-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="bbb1d-105">ASP.NET AJAX obsługuje operacje wykorzystujące zlecenia HTTP POST i HTTP GET z wartością domyślną POST protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="bbb1d-106">Podczas tworzenia operacji, która nie ma efektów ubocznych i zwraca dane, które rzadko lub nigdy nie są zmieniane, należy zamiast tego użyć protokołu HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="bbb1d-107">Wyniki operacji pobierania mogą być buforowane, co oznacza, że wiele wywołań tej samej operacji może spowodować tylko jedno żądanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="bbb1d-108">Buforowanie nie jest wykonywane przez program WCF, ale może być wykonywane na dowolnym poziomie (w przeglądarce użytkownika, na serwerze proxy i na innych poziomach). Buforowanie jest korzystne, jeśli chcesz zwiększyć wydajność usługi, ale może nie być akceptowalne, jeśli dane często ulegają zmianie lub jeśli operacja wykonuje pewne działania.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="bbb1d-109">Na przykład w przypadku projektowania usługi do zarządzania biblioteką muzyczną użytkownika, operacja, która wyszukuje wykonawcę na podstawie tytułu albumu z używania GET, ale operacja, która dodaje album do osobistej kolekcji użytkownika, musi używać wpisu POST.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="bbb1d-110">Aby kontrolować okres istnienia pamięci podręcznej, należy użyć <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="bbb1d-111">Na przykład podczas projektowania usługi, która zwraca prognozy pogody, które są aktualizowane co godzinę, należy użyć funkcji GET, ale ograniczyć czas trwania pamięci podręcznej na godzinę lub mniejszą, aby uniemożliwić użytkownikom usługi dostęp do starych danych.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="bbb1d-112">W przypadku korzystania z usług ze strony ASP.NET AJAX, która używa kontrolki Menedżera skryptów, nie ma żadnej różnicy niezależnie od tego, czy operacja korzysta z mechanizmu GET, czy po nim, zapewnia wydawanie prawidłowego typu żądania.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="bbb1d-113">Operacje HTTP GET używają wszelkich parametrów wejściowych obsługiwanych przez operacje POST, w tym złożone typy kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="bbb1d-114">Jednak w większości przypadków zaleca się uniknięcie zbyt wielu parametrów lub parametrów, które są zbyt złożone w operacjach pobierania, ponieważ zmniejsza to wydajność buforowania.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="bbb1d-115">W tym temacie przedstawiono sposób wybierania między poleceniem GET i POST przez <xref:System.ServiceModel.Web.WebGetAttribute> dodanie <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów lub do odpowiednich operacji w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="bbb1d-116">Pozostałe kroki (do wdrożenia, skonfigurowania i hostowania usługi), które są wymagane do uruchomienia usługi, są podobne do tych, które są używane przez dowolną ASP.NET AJAX usługi w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="bbb1d-117">Operacja oznaczona przy użyciu <xref:System.ServiceModel.Web.WebGetAttribute> zawsze używa żądania GET.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="bbb1d-118">Operacja oznaczona przy użyciu elementu <xref:System.ServiceModel.Web.WebInvokeAttribute> lub nie jest oznaczona z żadnym z tych dwóch atrybutów, używa żądania post.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="bbb1d-119"><xref:System.ServiceModel.Web.WebInvokeAttribute>Umożliwia korzystanie z innych czasowników HTTP, innych niż get i post (takich jak Put i Delete) za pośrednictwem <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="bbb1d-120">Jednak te czasowniki nie są obsługiwane przez ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="bbb1d-121">Jeśli zamierzasz używać usługi ze stron ASP.NET przy użyciu formantu Menedżera skryptów, nie używaj <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="bbb1d-122">Aby zapoznać się z przykładowym przełączaniem do pobrania, zobacz [podstawowe przykładowe usługi AJAX](../samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="bbb1d-122">For a working example of switching to GET, see the [Basic AJAX Service](../samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="bbb1d-123">Aby zapoznać się z przykładem korzystającym z funkcji POST, zapoznaj się z [usługą AJAX przy użyciu przykładu http post](../samples/ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="bbb1d-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="bbb1d-124">Aby utworzyć usługę WCF, która odpowiada na żądania HTTP GET lub HTTP POST</span><span class="sxs-lookup"><span data-stu-id="bbb1d-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="bbb1d-125">Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="bbb1d-126">Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bbb1d-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="bbb1d-127">Dodaj <xref:System.ServiceModel.Web.WebGetAttribute> atrybut, aby określić, że operacja powinna odpowiedzieć na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="bbb1d-128">Można również dodać <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut, aby jawnie określić wpis http, lub nie określić atrybutu, który domyślnie przyjmuje wartość http post.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="bbb1d-129">Zaimplementuj `IMusicService` kontrakt usługi za pomocą `MusicService` .</span><span class="sxs-lookup"><span data-stu-id="bbb1d-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="bbb1d-130">Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="bbb1d-131">Edytuj ten plik, dodając odpowiednie informacje o dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) dla usługi.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-131">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="bbb1d-132">Określ, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używana w dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) , aby automatycznie konfigurować punkt końcowy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="bbb1d-133">Aby wywołać usługę</span><span class="sxs-lookup"><span data-stu-id="bbb1d-133">To call the service</span></span>  
  
1. <span data-ttu-id="bbb1d-134">Możesz testować operacje pobrania usługi bez kodu klienta, korzystając z przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="bbb1d-135">Na przykład jeśli skonfigurowano usługę pod `http://example.com/service.svc` adresem, `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` nastąpi ponowne wprowadzenie do paska adresu przeglądarki i spowoduje, że odpowiedź zostanie pobrana lub wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="bbb1d-136">Usługi można używać w taki sam sposób jak inne usługi ASP.NET AJAX, wprowadzając adres URL usługi do kolekcji scripts formantu ASP.NET AJAX Script Manager.</span><span class="sxs-lookup"><span data-stu-id="bbb1d-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="bbb1d-137">Aby zapoznać się z przykładem, zobacz [podstawową usługę AJAX](../samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="bbb1d-137">For an example, see the [Basic AJAX Service](../samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bbb1d-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbb1d-138">See also</span></span>

- [<span data-ttu-id="bbb1d-139">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bbb1d-139">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="bbb1d-140">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="bbb1d-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
