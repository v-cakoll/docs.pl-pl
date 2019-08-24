---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 655e8807a78d542cd7fa586eca3750507891f74b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988775"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="a07c0-102">Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="a07c0-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="a07c0-103">umożliwia korzystanie z mechanizmu deklaracyjnej pamięci podręcznej, który jest już dostępny w ASP.NET w usługach HTTP sieci Web WCF.</span><span class="sxs-lookup"><span data-stu-id="a07c0-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="a07c0-104">Pozwala to na buforowanie odpowiedzi z operacji usługi HTTP sieci Web w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="a07c0-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="a07c0-105">Gdy użytkownik wysyła HTTP GET do usługi skonfigurowanej do buforowania, ASP.NET wysyła do tyłu buforowaną odpowiedź i metoda usługi nie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a07c0-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="a07c0-106">Gdy pamięć podręczna zostanie wygaśnie, następnym razem, gdy użytkownik wyśle HTTP GET, wywoływana jest metoda usługi i odpowiedź jest ponownie buforowana.</span><span class="sxs-lookup"><span data-stu-id="a07c0-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="a07c0-107">Aby uzyskać więcej informacji o pamięci podręcznej ASP.NET, zobacz [buforowanie ASP.NET — Omówienie](https://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="a07c0-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="a07c0-108">Podstawowe buforowanie usługi HTTP w sieci Web</span><span class="sxs-lookup"><span data-stu-id="a07c0-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="a07c0-109">Aby włączyć buforowanie usługi HTTP sieci Web, należy najpierw włączyć zgodność ASP.NET, stosując <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ustawienia <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> usługi lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="a07c0-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="a07c0-110">wprowadza nowy atrybut o nazwie <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , który umożliwia określenie nazwy profilu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a07c0-110">introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="a07c0-111">Ten atrybut jest stosowany do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a07c0-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="a07c0-112">W poniższym przykładzie zastosowano <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi, aby włączyć zgodność ASP.NET i `GetCustomer` skonfigurować operację buforowania.</span><span class="sxs-lookup"><span data-stu-id="a07c0-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="a07c0-113">Ten <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atrybut określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="a07c0-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 <span data-ttu-id="a07c0-114">Należy również włączyć tryb zgodności ASP.NET w pliku Web. config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a07c0-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="a07c0-115">Jeśli tryb zgodności ASP.NET nie jest włączony i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a07c0-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="a07c0-116">Nazwa profilu pamięci podręcznej określona <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> w identyfikatorze identyfikuje profil pamięci podręcznej, który jest dodawany do pliku konfiguracyjnego Web. config.</span><span class="sxs-lookup"><span data-stu-id="a07c0-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="a07c0-117">Profil pamięci podręcznej jest zdefiniowany za pomocą`outputCacheSetting`elementu w < >, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a07c0-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="a07c0-118">Jest to ten sam element konfiguracji, który jest dostępny dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a07c0-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="a07c0-119">Aby uzyskać więcej informacji na temat profili pamięci podręcznej ASP.NET, zobacz <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="a07c0-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="a07c0-120">W przypadku usług HTTP w sieci Web najważniejsze atrybuty w profilu pamięci podręcznej `cacheDuration` to `varyByParam`: i.</span><span class="sxs-lookup"><span data-stu-id="a07c0-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="a07c0-121">Oba te atrybuty są wymagane.</span><span class="sxs-lookup"><span data-stu-id="a07c0-121">Both of these attributes are required.</span></span> <span data-ttu-id="a07c0-122">`cacheDuration`Określa czas, przez jaki odpowiedź powinna być buforowana w sekundach.</span><span class="sxs-lookup"><span data-stu-id="a07c0-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="a07c0-123">`varyByParam`pozwala określić parametr ciągu zapytania, który jest używany do buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a07c0-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="a07c0-124">Wszystkie żądania z różnymi wartościami parametrów ciągu zapytania są buforowane osobno.</span><span class="sxs-lookup"><span data-stu-id="a07c0-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="a07c0-125">Na przykład po wykonaniu `http://MyServer/MyHttpService/MyOperation?param=10`wstępnego żądania wszystkie kolejne żądania wykonane przy użyciu tego samego identyfikatora URI zostałyby zwrócone w pamięci podręcznej (o ile nie upłynął czas trwania pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="a07c0-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="a07c0-126">Odpowiedzi dla podobnego żądania, które jest takie samo, ale ma inną wartość dla parametru ciągu zapytania parametru są buforowane osobno.</span><span class="sxs-lookup"><span data-stu-id="a07c0-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="a07c0-127">Jeśli nie chcesz, aby to oddzielne zachowanie w pamięci podręcznej, ustaw `varyByParam` wartość "Brak".</span><span class="sxs-lookup"><span data-stu-id="a07c0-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="a07c0-128">Zależność pamięci podręcznej SQL</span><span class="sxs-lookup"><span data-stu-id="a07c0-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="a07c0-129">Odpowiedzi usługi HTTP sieci Web mogą być również buforowane z zależnością pamięci podręcznej SQL.</span><span class="sxs-lookup"><span data-stu-id="a07c0-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="a07c0-130">Jeśli usługa HTTP sieci Web w programie WCF zależy od danych przechowywanych w bazie danych SQL, może być konieczne przechowanie odpowiedzi usługi i unieważnienie pamięci podręcznej w przypadku zmiany danych w tabeli bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="a07c0-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="a07c0-131">To zachowanie jest konfigurowane w całości w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="a07c0-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="a07c0-132">Najpierw należy zdefiniować parametry połączenia w elemencie <`connectionStrings`>.</span><span class="sxs-lookup"><span data-stu-id="a07c0-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="a07c0-133">Następnie należy włączyć zależność pamięci podręcznej SQL w`caching`ramach elementu < > w`system.web`elemencie < >, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a07c0-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="a07c0-134">W tym miejscu jest włączona zależność pamięci podręcznej SQL i ustawiono czas sondowania 1000 milisekund.</span><span class="sxs-lookup"><span data-stu-id="a07c0-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="a07c0-135">Za każdym razem, gdy upłynie czas sondowania tabela bazy danych jest sprawdzana pod kątem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="a07c0-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="a07c0-136">W przypadku wykrycia zmian zawartość pamięci podręcznej jest usuwana, a przy następnym wywołaniu operacji usługi jest buforowana Nowa odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="a07c0-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="a07c0-137">W <`sqlCacheDependency`elementu > dodać bazy danych i odwołać się do parametrów połączenia w elemencie`databases`< >, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a07c0-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="a07c0-138">Następnie należy skonfigurować ustawienia wyjściowej pamięci podręcznej w`caching`< > elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a07c0-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="a07c0-139">W tym miejscu czas trwania pamięci podręcznej wynosi `varyByParam` 60 sekund, jest ustawiony `sqlDependency` na wartość None i jest ustawiany na listę rozdzielaną średnikami nazw baz danych/tabel, rozdzielając je średnikami.</span><span class="sxs-lookup"><span data-stu-id="a07c0-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="a07c0-140">Po zmianie danych `MyTable` w buforowanej odpowiedzi dla operacji usługi jest usuwana, a po wywołaniu operacji jest generowana Nowa odpowiedź (przez wywołanie operacji usługi), w pamięci podręcznej i zwróconej do klienta.</span><span class="sxs-lookup"><span data-stu-id="a07c0-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a07c0-141">Aby ASP.NET uzyskać dostęp do bazy danych SQL, należy użyć [narzędzia rejestracji SQL Server ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="a07c0-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="a07c0-142">Ponadto należy zezwolić na dostęp odpowiednich kont użytkowników do bazy danych i tabeli.</span><span class="sxs-lookup"><span data-stu-id="a07c0-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="a07c0-143">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do SQL Server z aplikacji sieci Web](https://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="a07c0-143">For more information, see [Accessing SQL Server from a Web Application](https://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="a07c0-144">Buforowanie warunkowe oparte na protokole HTTP</span><span class="sxs-lookup"><span data-stu-id="a07c0-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="a07c0-145">W scenariuszach HTTP sieci Web warunkowe pobieranie HTTP jest często używane przez usługi do implementowania inteligentnego buforowania HTTP zgodnie z opisem w [specyfikacji protokołu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="a07c0-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="a07c0-146">Aby to zrobić, usługa musi ustawić wartość nagłówka ETag w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a07c0-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="a07c0-147">Należy również sprawdzić nagłówek If-None-Match w żądaniu HTTP, aby sprawdzić, czy którykolwiek z określonych elementów ETag jest zgodny z bieżącym elementem ETag.</span><span class="sxs-lookup"><span data-stu-id="a07c0-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="a07c0-148">W przypadku żądań GET i Web, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje wartość ETag i sprawdza ją w nagłówku If-None-Match żądania.</span><span class="sxs-lookup"><span data-stu-id="a07c0-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="a07c0-149">Jeśli nagłówek jest obecny i występuje dopasowanie, a <xref:System.ServiceModel.Web.WebFaultException> z kodem stanu HTTP 304 (niemodyfikowane) jest zgłaszany, a nagłówek ETag zostanie dodany do odpowiedzi z pasującym elementem ETag.</span><span class="sxs-lookup"><span data-stu-id="a07c0-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="a07c0-150">Jedno Przeciążenie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody przyjmuje datę ostatniej modyfikacji i sprawdza ją względem nagłówka If-Modified-od żądania.</span><span class="sxs-lookup"><span data-stu-id="a07c0-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="a07c0-151">Jeśli nagłówek jest obecny, a zasób nie został zmodyfikowany od momentu, <xref:System.ServiceModel.Web.WebFaultException> zostanie zgłoszony kod stanu HTTP 304 (niemodyfikowany).</span><span class="sxs-lookup"><span data-stu-id="a07c0-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="a07c0-152">W przypadku żądań <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Put, post i DELETE pobiera bieżącą wartość ETag zasobu.</span><span class="sxs-lookup"><span data-stu-id="a07c0-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="a07c0-153">Jeśli bieżąca wartość ETag ma wartość null, Metoda sprawdza, czy nagłówek If-None-Match ma wartość "\*".</span><span class="sxs-lookup"><span data-stu-id="a07c0-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="a07c0-154">Jeśli bieżąca wartość ETag nie jest wartością domyślną, Metoda sprawdza bieżącą wartość ETag w nagłówku If-Match żądania.</span><span class="sxs-lookup"><span data-stu-id="a07c0-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="a07c0-155">W obu przypadkach Metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> komunikat z kodem stanu HTTP 412 (warunek wstępny nie powiódł się), jeśli oczekiwany nagłówek nie występuje w żądaniu lub jego wartość nie spełnia warunkowego sprawdzania i ustawia nagłówek ETag odpowiedzi dla bieżącego elementu ETag wartościami.</span><span class="sxs-lookup"><span data-stu-id="a07c0-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="a07c0-156">`CheckConditional` Metody<xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> i metody zapewniają, że wartość ETag ustawiona w nagłówku odpowiedzi jest prawidłowym elementem ETag zgodnie ze specyfikacją protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a07c0-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="a07c0-157">Obejmuje to otaczającie wartości ETag w podwójnych cudzysłowach, jeśli nie są one jeszcze obecne i prawidłowo ucieczką znaków wewnętrznego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="a07c0-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="a07c0-158">Słabe porównanie ETag nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a07c0-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="a07c0-159">Poniższy przykład pokazuje, jak używać tych metod.</span><span class="sxs-lookup"><span data-stu-id="a07c0-159">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="a07c0-160">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a07c0-160">Security Considerations</span></span>  
 <span data-ttu-id="a07c0-161">Żądania, które wymagają autoryzacji, nie powinny mieć buforowanych odpowiedzi, ponieważ autoryzacja nie jest wykonywana, gdy odpowiedź jest obsługiwana z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a07c0-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="a07c0-162">Buforowanie takich odpowiedzi spowoduje powstanie poważnych luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="a07c0-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="a07c0-163">Zazwyczaj żądania, które wymagają autoryzacji, zapewniają dane specyficzne dla użytkownika i dlatego buforowanie po stronie serwera nie jest jeszcze korzystne.</span><span class="sxs-lookup"><span data-stu-id="a07c0-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="a07c0-164">W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowanie w ogóle będzie bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="a07c0-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
