---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 25b564235b5d2b3b26b5d657f3e5f0bd5d594125
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081313"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="2669f-102">Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="2669f-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="2669f-103"> Umożliwia użycie deklaratywne mechanizm buforowania, dostępnych w programie ASP.NET w usługach WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="2669f-103"> enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="2669f-104">Dzięki temu można buforowanie odpowiedzi z operacji usługi WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="2669f-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="2669f-105">Gdy użytkownik wysyła żądania HTTP GET do usługi, który jest skonfigurowany do buforowania, ASP.NET odsyła odpowiedzi z pamięci podręcznej i nie jest wywoływana metoda usługi.</span><span class="sxs-lookup"><span data-stu-id="2669f-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="2669f-106">Po wygaśnięciu pamięci podręcznej, następnym razem użytkownik wysyła żądania HTTP GET, wywoływana jest metoda swoje usługi i odpowiedź jest zbuforowana z jeszcze raz.</span><span class="sxs-lookup"><span data-stu-id="2669f-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="2669f-107">Aby uzyskać więcej informacji na temat buforowania platformy ASP.NET, zobacz [omówienie buforowania programu ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="2669f-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="2669f-108">Usługa HTTP Basic Web buforowania</span><span class="sxs-lookup"><span data-stu-id="2669f-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="2669f-109">Aby włączyć protokół HTTP sieci WEB usługi pamięci podręcznej, należy najpierw włączyć zgodność platformy ASP.NET, stosując <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do ustawienia usługi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="2669f-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="2669f-110"> wprowadza nowy atrybut o nazwie <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pozwala określić nazwę profilu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2669f-110"> introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="2669f-111">Ten atrybut jest stosowany do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="2669f-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="2669f-112">Następujący przykład dotyczy <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi, aby włączyć zgodności z platformą ASP.NET i konfiguruje `GetCustomer` operacji do buforowania.</span><span class="sxs-lookup"><span data-stu-id="2669f-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="2669f-113"><!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atrybut określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2669f-113">The <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
 <span data-ttu-id="2669f-114">Należy również włączyć tryb zgodności ASP.NET w pliku Web.config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2669f-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  <span data-ttu-id="2669f-115">Jeśli tryb zgodności ASP.NET nie jest włączona i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używana jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2669f-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="2669f-116">Nazwa profilu pamięci podręcznej, które są określone przez <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identyfikuje profil pamięci podręcznej, który jest dodawany do pliku konfiguracji Web.config.</span><span class="sxs-lookup"><span data-stu-id="2669f-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="2669f-117">Profil pamięci podręcznej jest zdefiniowana za pomocą w <`outputCacheSetting`> elementu, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2669f-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="2669f-118">Jest to ten sam element konfiguracji, która jest dostępna dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2669f-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="2669f-119">Aby uzyskać więcej informacji na temat profilów w pamięci podręcznej programu ASP.NET, zobacz <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="2669f-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="2669f-120">Dla usług HTTP w sieci Web są najważniejsze atrybutów w pamięci podręcznej profilu: `cacheDuration` i `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="2669f-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="2669f-121">Te atrybuty są wymagane.</span><span class="sxs-lookup"><span data-stu-id="2669f-121">Both of these attributes are required.</span></span> <span data-ttu-id="2669f-122">`cacheDuration` Określa ilość czasu, które mają być buforowane odpowiedzi w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="2669f-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="2669f-123">`varyByParam` Pozwala określić parametr ciągu zapytania używanego do buforowanie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2669f-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="2669f-124">Wszystkie żądania przekazywane za inne wartości parametrów ciągów są buforowane osobno.</span><span class="sxs-lookup"><span data-stu-id="2669f-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="2669f-125">Na przykład, po nawiązaniu początkowego żądania do http://MyServer/MyHttpService/MyOperation?param=10 wszystkich kolejnych żądań wykonywanych przy użyciu tego samego identyfikatora URI zostałyby zwrócone w odpowiedzi z pamięci podręcznej (, dopóki nie upłynie czas trwania pamięci podręcznej).</span><span class="sxs-lookup"><span data-stu-id="2669f-125">For example, once an initial request is made to http://MyServer/MyHttpService/MyOperation?param=10 all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="2669f-126">Odpowiedzi dla podobne żądania, która jest taka sama, ale ma inną wartość dla parametru ciągu zapytania parametr są buforowane osobno.</span><span class="sxs-lookup"><span data-stu-id="2669f-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="2669f-127">Jeśli nie mają oddzielne zachowania buforowania, ustaw `varyByParam` na "none".</span><span class="sxs-lookup"><span data-stu-id="2669f-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="2669f-128">Zależności pamięci podręcznej SQL</span><span class="sxs-lookup"><span data-stu-id="2669f-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="2669f-129">Odpowiedzi usługi HTTP sieci Web można buforować w taki sposób, w przypadku zależności pamięci podręcznej SQL.</span><span class="sxs-lookup"><span data-stu-id="2669f-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="2669f-130">Jeśli usługi WCF Web HTTP jest zależna od danych przechowywanych w bazie danych SQL, można buforować odpowiedzi usługi i unieważnić buforowaną odpowiedź, gdy danych w SQL bazy danych zmian w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2669f-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="2669f-131">To zachowanie jest całkowicie skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="2669f-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="2669f-132">Należy określić ciąg połączenia w <`connectionStrings`> element.</span><span class="sxs-lookup"><span data-stu-id="2669f-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="2669f-133">Następnie należy włączyć zależności pamięci podręcznej SQL w ramach <`caching`> elemencie <`system.web`> elementu, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2669f-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="2669f-134">W tym miejscu zależności pamięci podręcznej SQL jest włączona i ustawiono czas sondowania 1000 milisekund.</span><span class="sxs-lookup"><span data-stu-id="2669f-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="2669f-135">Każdorazowo podczas sondowania upływa tabeli bazy danych jest sprawdzane pod kątem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="2669f-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="2669f-136">Jeśli wykryto zmiany zawartości pamięci podręcznej są usuwane, a przy następnej operacji usługi jest wywoływany nowej odpowiedzi są buforowane.</span><span class="sxs-lookup"><span data-stu-id="2669f-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="2669f-137">W ramach <`sqlCacheDependency`> elementu Dodawanie baz danych i odwoływać się do parametrów połączenia w ramach <`databases`> elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2669f-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="2669f-138">Następnie należy skonfigurować ustawienia wyjściowej pamięci podręcznej w ramach <`caching`> elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2669f-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="2669f-139">W tym miejscu czas trwania pamięci podręcznej jest ustawiona na 60 sekund, `varyByParam` jest ustawiona na wartość none i `sqlDependency` ustawiono rozdzielaną średnikami listę par nazwa/table bazy danych, rozdzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="2669f-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="2669f-140">Gdy dane w `MyTable` zostanie zmieniony buforowane odpowiedzi dla operacji usługi zostanie usunięty, a podczas wywoływania operacji nowej odpowiedzi wygenerowanych (według wywoływanie operacji usługi), pamięci podręcznej i zwracany do klienta.</span><span class="sxs-lookup"><span data-stu-id="2669f-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2669f-141">W technologii ASP.NET dostępu do bazy danych SQL, należy użyć [narzędzia rejestracji serwera SQL platformy ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="2669f-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="2669f-142">Ponadto muszą zezwalać na do odpowiedniego dostępu do bazy danych i tabeli.</span><span class="sxs-lookup"><span data-stu-id="2669f-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="2669f-143">Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do programu SQL Server z aplikacji sieci Web](https://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="2669f-143">For more information, see [Accessing SQL Server from a Web Application](https://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="2669f-144">Warunkowe UZYSKAĆ oparty na protokole HTTP buforowania</span><span class="sxs-lookup"><span data-stu-id="2669f-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="2669f-145">W scenariuszach protokołu HTTP sieci Web warunkowego HTTP GET jest często używana przez usługi do zaimplementowania buforowania inteligentnego HTTP, zgodnie z opisem w [specyfikację protokołu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="2669f-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="2669f-146">W tym celu usługa należy ustawić wartość nagłówka ETag w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="2669f-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="2669f-147">On także sprawdzić nagłówek If-None-Match w żądaniu HTTP, aby sprawdzić, czy dowolny element ETag określony odpowiada bieżący element ETag.</span><span class="sxs-lookup"><span data-stu-id="2669f-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="2669f-148">W przypadku żądań GET i HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje wartość elementu ETag i porównuje ją z nagłówka If-None-Match żądania.</span><span class="sxs-lookup"><span data-stu-id="2669f-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="2669f-149">Nagłówek jest obecny, jeśli ma dopasowania <xref:System.ServiceModel.Web.WebFaultException> za pośrednictwem protokołu HTTP jest generowany kod stanu 304 (nie zmodyfikowano), a nagłówka ETag jest dodawany do odpowiedzi z pasującego tagu ETag.</span><span class="sxs-lookup"><span data-stu-id="2669f-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="2669f-150">Jednego przeciążenia <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda przyjmuje daty ostatniej modyfikacji i porównuje ją z nagłówka If-Modified-Since żądania.</span><span class="sxs-lookup"><span data-stu-id="2669f-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="2669f-151">Jeśli nagłówek a zasób nie został zmodyfikowany od czasu, <xref:System.ServiceModel.Web.WebFaultException> za pośrednictwem protokołu HTTP jest generowany kod stanu 304 (nie zmodyfikowano).</span><span class="sxs-lookup"><span data-stu-id="2669f-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="2669f-152">Dla żądania PUT, POST i DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> przyjmuje bieżącej wartości zasobu element ETag.</span><span class="sxs-lookup"><span data-stu-id="2669f-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="2669f-153">Jeśli bieżąca wartość elementu ETag ma wartość null, metoda sprawdza, czy nagłówek If-None-Match ma wartość "\*".</span><span class="sxs-lookup"><span data-stu-id="2669f-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="2669f-154">Jeśli bieżąca wartość elementu ETag nie jest wartość domyślna, metoda sprawdza bieżącą wartość elementu ETag dla nagłówka If - Match żądania.</span><span class="sxs-lookup"><span data-stu-id="2669f-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="2669f-155">W obu przypadkach, metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> ze stanem HTTP kodu oczekiwano nagłówka nie znajduje się w żądaniu lub jego wartość nie spełnia warunkowego wyboru i ustawia dla nagłówka ETag odpowiedzi na bieżący element ETag 412 (niepowodzenie warunku wstępnego) wartość.</span><span class="sxs-lookup"><span data-stu-id="2669f-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="2669f-156">Zarówno `CheckConditional` metod i <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda gwarantuje, że wartość elementu ETag w nagłówku odpowiedzi jest prawidłowy element ETag zgodnie ze specyfikacją protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2669f-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="2669f-157">Obejmuje to otaczające wartość elementu ETag w cudzysłów, jeśli nie są jeszcze obecne i prawidłowo anulowania zapewnianego element znaków wewnętrznego podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="2669f-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="2669f-158">Słabe porównania element ETag nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2669f-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="2669f-159">Poniższy przykład przedstawia sposób użycia tych metod.</span><span class="sxs-lookup"><span data-stu-id="2669f-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="2669f-160">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2669f-160">Security Considerations</span></span>  
 <span data-ttu-id="2669f-161">Żądania, które wymagają autoryzacji nie powinny mieć ich odpowiedzi w pamięci podręcznej, ponieważ autoryzacji nie jest przeprowadzane, gdy odpowiedź jest obsługiwany z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="2669f-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="2669f-162">Buforowanie odpowiedzi na takie spowodowałoby to powstanie luk w zabezpieczeniach z powodu poważnego naruszenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2669f-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="2669f-163">Zazwyczaj żądania, które wymagają autoryzacji dostarczać dane specyficzne dla użytkownika, i w związku z tym buforowanie po stronie serwera nie jest nawet korzystne.</span><span class="sxs-lookup"><span data-stu-id="2669f-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="2669f-164">W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowania w ogóle będzie bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="2669f-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
