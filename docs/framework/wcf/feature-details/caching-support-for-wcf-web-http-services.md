---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 8272ece5fcaf395b0ec8191afae8eabc998c7f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="50b2c-102">Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="50b2c-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="50b2c-103"> Umożliwia korzystanie z deklaratywne mechanizm buforowania już dostępne w programie ASP.NET w usługach WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="50b2c-103"> enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="50b2c-104">Dzięki temu można do pamięci podręcznej odpowiedzi z operacji usługi WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="50b2c-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="50b2c-105">Gdy użytkownik wysyła do usługi, który jest skonfigurowany dla buforowania GET protokołu HTTP, ASP.NET odsyła odpowiedź buforowana i nie wywołano metody usługi.</span><span class="sxs-lookup"><span data-stu-id="50b2c-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="50b2c-106">Po wygaśnięciu pamięci podręcznej, przy następnym użytkownik wysyła HTTP GET, jest wywoływana przez metodę usługi i ponownie buforowaną odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="50b2c-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="50b2c-107">Aby uzyskać więcej informacji na temat buforowania platformy ASP.NET, zobacz [omówienie pamięci podręcznej programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="50b2c-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](http://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="50b2c-108">Usługa HTTP sieci Web podstawowe buforowanie</span><span class="sxs-lookup"><span data-stu-id="50b2c-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="50b2c-109">Aby włączyć protokół HTTP sieci WEB usługi buforowania, należy najpierw włączyć zgodności z platformą ASP.NET, stosując <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do ustawienia usługi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="50b2c-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="50b2c-110"> wprowadzono nowy atrybut o nazwie <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> który pozwala określić nazwę profilu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="50b2c-110"> introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="50b2c-111">Ten atrybut jest stosowany do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="50b2c-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="50b2c-112">Następujący przykład dotyczy <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi w celu włączenia zgodności z platformą ASP.NET i konfiguruje `GetCustomer` operacji do buforowania.</span><span class="sxs-lookup"><span data-stu-id="50b2c-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="50b2c-113"><!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atrybut określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej do użycia.</span><span class="sxs-lookup"><span data-stu-id="50b2c-113">The <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
 <span data-ttu-id="50b2c-114">Należy również włączyć tryb zgodności ASP.NET w pliku Web.config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="50b2c-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  <span data-ttu-id="50b2c-115">Jeśli nie włączono tryb zgodności ASP.NET i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używany jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="50b2c-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="50b2c-116">Nazwa profilu pamięci podręcznej, określony przez <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identyfikuje profil pamięci podręcznej, który jest dodawany do pliku konfiguracji Web.config.</span><span class="sxs-lookup"><span data-stu-id="50b2c-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="50b2c-117">Profil pamięci podręcznej jest zdefiniowana z w <`outputCacheSetting`> element, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50b2c-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="50b2c-118">Jest to tego samego elementu konfiguracji, która jest dostępna dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="50b2c-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="50b2c-119">Aby uzyskać więcej informacji na temat profilów pamięci podręcznej programu ASP.NET, zobacz <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="50b2c-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="50b2c-120">Dla usług HTTP sieci Web, są najważniejsze atrybuty w profilu pamięci podręcznej: `cacheDuration` i `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="50b2c-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="50b2c-121">Oba te atrybuty są wymagane.</span><span class="sxs-lookup"><span data-stu-id="50b2c-121">Both of these attributes are required.</span></span> <span data-ttu-id="50b2c-122">`cacheDuration` Ustawia czas, które mają być buforowane odpowiedzi w sekundach.</span><span class="sxs-lookup"><span data-stu-id="50b2c-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="50b2c-123">`varyByParam` można określić parametr ciągu zapytania używanego do odpowiedzi z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="50b2c-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="50b2c-124">Wszystkie żądania z wartościami parametrów ciągu zapytania różnych są buforowane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="50b2c-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="50b2c-125">Na przykład po wysłaniu żądania początkowego do http://MyServer/MyHttpService/MyOperation?param=10 wszystkie kolejne żądania o tym samym identyfikatorze URI będzie zwracany buforowanej odpowiedzi (o ile nie upłynął czas trwania pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="50b2c-125">For example, once an initial request is made to http://MyServer/MyHttpService/MyOperation?param=10 all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="50b2c-126">Odpowiedzi na żądania podobne jest taki sam, ale ma inną wartość dla parametru ciągu zapytania parametru są buforowane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="50b2c-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="50b2c-127">Jeśli nie chcesz, aby to zachowanie buforowania w oddzielnych, ustaw `varyByParam` "none".</span><span class="sxs-lookup"><span data-stu-id="50b2c-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="50b2c-128">Zależności bufora SQL</span><span class="sxs-lookup"><span data-stu-id="50b2c-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="50b2c-129">Odpowiedzi usługi HTTP sieci Web można buforować w taki sposób, w zależności buforu SQL.</span><span class="sxs-lookup"><span data-stu-id="50b2c-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="50b2c-130">Jeśli usługi WCF Web HTTP zależy od danych przechowywanych w bazie danych SQL, można buforować odpowiedzi usługi akcji i unieważnić buforowanej odpowiedzi podczas zmiany tabeli bazy danych SQL danych.</span><span class="sxs-lookup"><span data-stu-id="50b2c-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="50b2c-131">To zachowanie jest całkowicie skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="50b2c-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="50b2c-132">Należy określić parametry połączenia w <`connectionStrings`> elementu.</span><span class="sxs-lookup"><span data-stu-id="50b2c-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="50b2c-133">Następnie należy włączyć zależność buforu SQL w ramach <`caching`> w elemencie <`system.web`> element, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="50b2c-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="50b2c-134">W tym miejscu zależności bufora SQL jest włączona i godzina sondowania, 1000 milisekund jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="50b2c-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="50b2c-135">Zawsze sondowania upłynie tabeli bazy danych jest sprawdzany pod kątem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="50b2c-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="50b2c-136">Jeśli zostaną wykryte zmiany zawartość pamięci podręcznej są usuwane i przy następnej operacji usługi jest wywoływany nowej odpowiedzi są buforowane.</span><span class="sxs-lookup"><span data-stu-id="50b2c-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="50b2c-137">W ramach <`sqlCacheDependency`> element Dodaj bazy danych i referencyjne parametry połączenia w <`databases`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="50b2c-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="50b2c-138">Następnie należy skonfigurować ustawienia wyjściowej pamięci podręcznej w <`caching`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="50b2c-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="50b2c-139">W tym miejscu czas buforowania ma ustawioną wartość 60 sekund, `varyByParam` ma wartość none i `sqlDependency` ma ustawioną wartość listy rozdzielanych średnikami oddzielone dwukropkiem pary nazwa/tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="50b2c-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="50b2c-140">Gdy dane w `MyTable` zostanie zmieniona buforowanej odpowiedzi dla operacji usługi zostanie usunięty i po wywołaniu operacji nową odpowiedź jest generowany (przez wywołanie operacji usługi), w pamięci podręcznej i zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="50b2c-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50b2c-141">Dla platformy ASP.NET dostępu do bazy danych SQL, należy użyć [ASP.NET SQL Server Registration Tool](http://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="50b2c-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](http://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="50b2c-142">Ponadto musisz zezwolić na odpowiedniego użytkownika konta dostępu do bazy danych i tabeli.</span><span class="sxs-lookup"><span data-stu-id="50b2c-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="50b2c-143">Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do programu SQL Server z aplikacji sieci Web](http://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="50b2c-143">For more information, see [Accessing SQL Server from a Web Application](http://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="50b2c-144">Warunkowe HTTP GET na podstawie buforowanie</span><span class="sxs-lookup"><span data-stu-id="50b2c-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="50b2c-145">W scenariuszach protokołu HTTP sieci Web warunkowego HTTP GET jest często używane przez usługi do zaimplementowania inteligentne buforowanie HTTP zgodnie z opisem w [specyfikacji HTTP](http://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="50b2c-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](http://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="50b2c-146">W tym celu usługi należy ustawić wartość nagłówka ETag w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="50b2c-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="50b2c-147">On również sprawdzić nagłówka If-None-Match w żądaniu HTTP, czy dowolne ETag określony odpowiada bieżącej ETag.</span><span class="sxs-lookup"><span data-stu-id="50b2c-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="50b2c-148">Dla żądania GET i HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje wartość ETag i porównuje ją z nagłówka If-None-Match żądania.</span><span class="sxs-lookup"><span data-stu-id="50b2c-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="50b2c-149">Jeśli istnieje nagłówek i są zgodne, <xref:System.ServiceModel.Web.WebFaultException> protokołu HTTP jest generowany kod stanu 304 (nie jest modyfikowany) i dodaniu nagłówka ETag do odpowiedzi z pasującego tagu ETag.</span><span class="sxs-lookup"><span data-stu-id="50b2c-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="50b2c-150">Jednego przeciążenia <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda pobiera daty ostatniej modyfikacji i porównuje ją z nagłówka If-Modified-Since żądania.</span><span class="sxs-lookup"><span data-stu-id="50b2c-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="50b2c-151">Jeśli istnieje nagłówek i zasób nie został zmodyfikowany od czasu, <xref:System.ServiceModel.Web.WebFaultException> protokołu HTTP jest generowany kod stanu 304 (nie jest modyfikowany).</span><span class="sxs-lookup"><span data-stu-id="50b2c-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="50b2c-152">Dla żądania PUT, POST i DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> przejście do bieżącej wartości ETag dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="50b2c-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="50b2c-153">Jeśli do bieżącej wartości ETag ma wartość null, metoda sprawdza, czy nagłówek If-None-Match ma wartość "\*".</span><span class="sxs-lookup"><span data-stu-id="50b2c-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="50b2c-154">Jeśli do bieżącej wartości ETag nie jest wartością domyślną, metoda sprawdza do bieżącej wartości ETag dla nagłówka If - Match żądania.</span><span class="sxs-lookup"><span data-stu-id="50b2c-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="50b2c-155">W obu przypadkach metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> ze stanem HTTP code oczekiwano nagłówka nie znajduje się w żądaniu lub jego wartość nie spełnia warunkowego sprawdzenia i ustawia nagłówek ETag odpowiedzi do bieżącego tagu ETag 412 (warunek wstępny nie powiodła się.) wartość.</span><span class="sxs-lookup"><span data-stu-id="50b2c-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="50b2c-156">Zarówno `CheckConditional` metod i <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> — metoda gwarantuje, że wartość ETag w nagłówku odpowiedzi jest prawidłowy element ETag według specyfikacji HTTP.</span><span class="sxs-lookup"><span data-stu-id="50b2c-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="50b2c-157">Obejmuje to otaczającego wartość ETag w podwójne cudzysłowy, jeśli nie istnieją już i poprawnie anulowanie znaków podwójnego cudzysłowu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="50b2c-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="50b2c-158">Słaby element ETag porównania nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="50b2c-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="50b2c-159">Poniższy przykład przedstawia sposób użycia tych metod.</span><span class="sxs-lookup"><span data-stu-id="50b2c-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="50b2c-160">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="50b2c-160">Security Considerations</span></span>  
 <span data-ttu-id="50b2c-161">Żądania, które wymagają autoryzacji nie powinna mieć odpowiedzi pamięci podręcznej, autoryzacji nie jest wykonywana po udostępnieniu odpowiedzi z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="50b2c-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="50b2c-162">Buforowanie odpowiedzi na takie spowodowałoby to powstanie luki w zabezpieczeniach poważne.</span><span class="sxs-lookup"><span data-stu-id="50b2c-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="50b2c-163">Zazwyczaj żądania, które wymagają autoryzacji zawierają dane specyficzne dla użytkownika i dlatego buforowanie po stronie serwera nie jest jeszcze korzystne.</span><span class="sxs-lookup"><span data-stu-id="50b2c-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="50b2c-164">W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowanie na wszystkich będą bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="50b2c-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
