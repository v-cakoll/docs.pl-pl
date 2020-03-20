---
title: 'Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184753"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="281a1-102">Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="281a1-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="281a1-103">Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia ASP.NET punkt końcowy z obsługą AJAX, który można wywołać z języka JavaScript w witrynie sieci Web klienta.</span><span class="sxs-lookup"><span data-stu-id="281a1-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="281a1-104">Podstawowe procedury tworzenia takich usług zostały omówione w artykule [Jak: Użyj konfiguracji, aby dodać ASP.NET punkt końcowy AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) i [Jak: Dodaj ASP.NET punkt końcowy AJAX bez użycia konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="281a1-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="281a1-105">ASP.NET AJAX obsługuje operacje korzystające z zleceń HTTP POST i HTTP GET, przy czym domyślnym ustawieniem jest protokół HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="281a1-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="281a1-106">Podczas tworzenia operacji, która nie ma skutków ubocznych i zwraca dane, które rzadko lub nigdy się nie zmienia, należy użyć HTTP GET zamiast.</span><span class="sxs-lookup"><span data-stu-id="281a1-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="281a1-107">Wyniki operacji GET mogą być buforowane, co oznacza, że wiele wywołań tej samej operacji może spowodować tylko jedno żądanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="281a1-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="281a1-108">Buforowanie nie jest wykonywane przez WCF, ale może odbywać się na dowolnym poziomie (w przeglądarce użytkownika, na serwerze proxy i innych poziomach). Buforowanie jest korzystne, jeśli chcesz zwiększyć wydajność usługi, ale może nie być dopuszczalne, jeśli dane często się zmieniają lub jeśli operacja wykonuje pewne działania.</span><span class="sxs-lookup"><span data-stu-id="281a1-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="281a1-109">Na przykład jeśli projektujesz usługę do zarządzania biblioteką muzyczną użytkownika, operacja, która wyszukuje wykonawcę na podstawie tytułu albumu, korzysta z użycia GET, ale operacja, która dodaje album do osobistej kolekcji użytkownika, musi używać postu.</span><span class="sxs-lookup"><span data-stu-id="281a1-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="281a1-110">Aby kontrolować okres istnienia pamięci <xref:System.ServiceModel.Web.OutgoingWebResponseContext> podręcznej, należy użyć typu.</span><span class="sxs-lookup"><span data-stu-id="281a1-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="281a1-111">Na przykład podczas projektowania usługi, która zwraca prognozy pogody aktualizowane co godzinę, należy użyć GET, ale ograniczyć czas trwania pamięci podręcznej do godziny lub mniej, aby uniemożliwić użytkownikom usługi dostęp do starych danych.</span><span class="sxs-lookup"><span data-stu-id="281a1-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="281a1-112">Podczas korzystania z usług ze strony ASP.NET AJAX, które używają formantu Menedżera skryptów, nie ma znaczenia, czy operacja używa GET lub POST — mechanizm menedżera skryptów zapewnia, że zostanie wystawiony poprawny typ żądania.</span><span class="sxs-lookup"><span data-stu-id="281a1-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="281a1-113">Operacje HTTP GET używają dowolnych parametrów wejściowych obsługiwanych przez operacje POST, w tym złożonych typów kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="281a1-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="281a1-114">Jednak w większości przypadków zaleca się unikanie zbyt wielu parametrów lub parametrów, które są zbyt złożone w operacjach GET, ponieważ zmniejsza wydajność buforowania.</span><span class="sxs-lookup"><span data-stu-id="281a1-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="281a1-115">W tym temacie pokazano, jak wybrać między <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> GET i POST, dodając lub atrybuty do odpowiednich operacji w umowie serwisowej.</span><span class="sxs-lookup"><span data-stu-id="281a1-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="281a1-116">Inne kroki (do zaimplementowania, skonfigurować i obsługiwać usługę), które są wymagane do uruchomienia usługi są podobne do tych używanych przez dowolny ASP.NET usługi AJAX w WCF.</span><span class="sxs-lookup"><span data-stu-id="281a1-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="281a1-117">Operacja oznaczona <xref:System.ServiceModel.Web.WebGetAttribute> zawsze używa żądania GET.</span><span class="sxs-lookup"><span data-stu-id="281a1-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="281a1-118">Operacja oznaczona <xref:System.ServiceModel.Web.WebInvokeAttribute>, lub nie oznaczona dowolnym z dwóch atrybutów, używa żądania POST.</span><span class="sxs-lookup"><span data-stu-id="281a1-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="281a1-119">Umożliwia <xref:System.ServiceModel.Web.WebInvokeAttribute> korzystanie z innych zleceń HTTP, innych niż GET i POST <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> (takich jak PUT i DELETE) za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="281a1-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="281a1-120">Jednak te zlecenia nie są obsługiwane przez ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="281a1-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="281a1-121">Jeśli zamierzasz korzystać z usługi z ASP.NET stron za pomocą formantu Menedżera skryptów, nie należy używać <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="281a1-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="281a1-122">Aby uzyskać działający przykład przełączania do GET, zobacz przykład [podstawowej usługi AJAX.](../../../../docs/framework/wcf/samples/basic-ajax-service.md)</span><span class="sxs-lookup"><span data-stu-id="281a1-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="281a1-123">Przykładowy używany post można znaleźć w przykładzie usługi AJAX przy użyciu protokołu [HTTP POST.](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)</span><span class="sxs-lookup"><span data-stu-id="281a1-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="281a1-124">Aby utworzyć usługę WCF, która odpowiada na żądania HTTP GET lub HTTP POST</span><span class="sxs-lookup"><span data-stu-id="281a1-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="281a1-125">Zdefiniuj podstawową umowę serwisową <xref:System.ServiceModel.ServiceContractAttribute> WCF za pomocą interfejsu oznaczonego atrybutem.</span><span class="sxs-lookup"><span data-stu-id="281a1-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="281a1-126">Oznacz każdą operację <xref:System.ServiceModel.OperationContractAttribute>za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="281a1-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="281a1-127">Dodaj <xref:System.ServiceModel.Web.WebGetAttribute> atrybut, aby określić, że operacja powinna odpowiadać na żądania HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="281a1-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="281a1-128">Można również dodać <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut, aby jawnie określić HTTP POST lub nie określić atrybutu, który domyślnie jest HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="281a1-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="281a1-129">`IMusicService` Zaimplementuj `MusicService`umowę serwisową z programem .</span><span class="sxs-lookup"><span data-stu-id="281a1-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="281a1-130">Utwórz nowy plik o nazwie usługa z rozszerzeniem .svc w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="281a1-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="281a1-131">Edytuj ten plik, [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dodając odpowiednie informacje o dyrektywie ServiceHost dla usługi.</span><span class="sxs-lookup"><span data-stu-id="281a1-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="281a1-132">Określ, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> że ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować ASP.NET punktu końcowego AJAX.</span><span class="sxs-lookup"><span data-stu-id="281a1-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="281a1-133">Aby zadzwonić do usługi</span><span class="sxs-lookup"><span data-stu-id="281a1-133">To call the service</span></span>  
  
1. <span data-ttu-id="281a1-134">Można przetestować operacje GET usługi bez kodu klienta, za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="281a1-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="281a1-135">Na przykład jeśli usługa jest skonfigurowana `http://example.com/service.svc` pod adresem, a następnie wpisanie `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` na pasku adresu przeglądarki wywołuje usługę i powoduje, że odpowiedź ma zostać pobrana lub wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="281a1-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="281a1-136">Usługi z operacjami GET można używać w taki sam sposób, jak w przypadku innych usług ASP.NET usługi AJAX — wprowadzając adres URL usługi w kolekcji Skrypty formantu ASP.NET menedżera skryptów AJAX.</span><span class="sxs-lookup"><span data-stu-id="281a1-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="281a1-137">Na przykład zobacz [podstawową usługę AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="281a1-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="281a1-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="281a1-138">See also</span></span>

- [<span data-ttu-id="281a1-139">Tworzenie usług WCF w technologii AJAX na platformie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="281a1-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="281a1-140">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="281a1-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
