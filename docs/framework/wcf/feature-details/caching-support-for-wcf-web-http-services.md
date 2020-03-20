---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 63c83cc1af9a3ccfdbdd79f8d0480e6c29eaf2f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185431"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="8846e-102">Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="8846e-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="8846e-103">umożliwia użycie mechanizmu buforowania deklaratywnego już dostępnego w ASP.NET w usługach HTTP w sieci Web WCF.</span><span class="sxs-lookup"><span data-stu-id="8846e-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="8846e-104">Dzięki temu można buforować odpowiedzi z operacji usługi WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="8846e-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="8846e-105">Gdy użytkownik wysyła HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET wysyła z powrotem buforowanej odpowiedzi i metoda usługi nie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8846e-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="8846e-106">Po wygaśnięciu pamięci podręcznej, następnym razem, gdy użytkownik wysyła HTTP GET, metoda usługi jest wywoływana i odpowiedź jest ponownie buforowane.</span><span class="sxs-lookup"><span data-stu-id="8846e-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="8846e-107">Aby uzyskać więcej informacji na temat ASP.NET buforowania, zobacz [ASP.NET Omówienie buforowania](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8846e-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="8846e-108">Buforowanie podstawowej usługi HTTP w sieci Web</span><span class="sxs-lookup"><span data-stu-id="8846e-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="8846e-109">Aby włączyć buforowanie usługi HTTP w sieci WEB, należy najpierw włączyć <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET zgodność, stosując ustawienie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> usługi do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="8846e-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="8846e-110">.NET Framework 4 wprowadza nowy <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atrybut o nazwie, który pozwala określić nazwę profilu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8846e-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="8846e-111">Ten atrybut jest stosowany do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8846e-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="8846e-112">Poniższy przykład stosuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi, aby włączyć zgodność ASP.NET i `GetCustomer` konfiguruje operację buforowania.</span><span class="sxs-lookup"><span data-stu-id="8846e-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="8846e-113">Atrybut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="8846e-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
<span data-ttu-id="8846e-114">Włącz również tryb zgodności ASP.NET w pliku Web.config, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8846e-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="8846e-115">Jeśli ASP.NET tryb zgodności nie jest włączony i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8846e-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="8846e-116">Nazwa profilu pamięci podręcznej określona <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> przez profil pamięci podręcznej, który jest dodawany do pliku konfiguracji Web.config.</span><span class="sxs-lookup"><span data-stu-id="8846e-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="8846e-117">Profil pamięci podręcznej jest zdefiniowany `outputCacheSetting` w <> element, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8846e-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="8846e-118">Jest to ten sam element konfiguracji, który jest dostępny dla ASP.NET aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8846e-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="8846e-119">Aby uzyskać więcej informacji na temat <xref:System.Web.Configuration.OutputCacheProfile>ASP.NET profili pamięci podręcznej, zobacz .</span><span class="sxs-lookup"><span data-stu-id="8846e-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="8846e-120">W przypadku usług HTTP w sieci Web najważniejsze `cacheDuration` `varyByParam`atrybuty w profilu pamięci podręcznej to: i .</span><span class="sxs-lookup"><span data-stu-id="8846e-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="8846e-121">Oba te atrybuty są wymagane.</span><span class="sxs-lookup"><span data-stu-id="8846e-121">Both of these attributes are required.</span></span> <span data-ttu-id="8846e-122">`cacheDuration`ustawia czas, przez który odpowiedź powinna być buforowana w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="8846e-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="8846e-123">`varyByParam`umożliwia określenie parametru ciągu zapytania, który jest używany do buforowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8846e-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="8846e-124">Wszystkie żądania wykonane z różnymi wartościami parametrów ciągu zapytania są buforowane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="8846e-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="8846e-125">Na przykład po pierwszym żądaniu `http://MyServer/MyHttpService/MyOperation?param=10`jest do , wszystkie kolejne żądania wykonane z tym samym identyfikatorem URI zostaną zwrócone buforowanej odpowiedzi (tak długo, jak czas trwania pamięci podręcznej nie upłynął).</span><span class="sxs-lookup"><span data-stu-id="8846e-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="8846e-126">Odpowiedzi na podobne żądanie, które jest takie samo, ale ma inną wartość dla parametru parametru parametru ciąg zapytania są buforowane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="8846e-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="8846e-127">Jeśli nie chcesz tego oddzielnego zachowania `varyByParam` buforowania, ustaw na "none".</span><span class="sxs-lookup"><span data-stu-id="8846e-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="8846e-128">Zależność pamięci podręcznej SQL</span><span class="sxs-lookup"><span data-stu-id="8846e-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="8846e-129">Odpowiedzi na usługi HTTP sieci Web mogą być również buforowane z zależnością pamięci podręcznej SQL.</span><span class="sxs-lookup"><span data-stu-id="8846e-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="8846e-130">Jeśli usługa WCF Web HTTP zależy od danych przechowywanych w bazie danych SQL, można buforować odpowiedź usługi i unieważnić buforowaną odpowiedź, gdy dane w tabeli bazy danych SQL ulegną zmianie.</span><span class="sxs-lookup"><span data-stu-id="8846e-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="8846e-131">To zachowanie jest całkowicie skonfigurowane w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="8846e-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="8846e-132">Najpierw zdefiniuj parametry połączenia `connectionStrings` w <> element.</span><span class="sxs-lookup"><span data-stu-id="8846e-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="8846e-133">Następnie należy włączyć zależność pamięci podręcznej `caching` SQL w <> element `system.web` w <> element, jak pokazano w poniższym przykładzie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8846e-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="8846e-134">W tym miejscu jest włączona zależność pamięci podręcznej SQL i ustawiony jest czas sondowania 1000 milisekund.</span><span class="sxs-lookup"><span data-stu-id="8846e-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="8846e-135">Za każdym razem, gdy czas sondowania upływa tabela bazy danych jest sprawdzany pod kątem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8846e-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="8846e-136">Jeśli zostaną wykryte zmiany zawartość pamięci podręcznej są usuwane i następnym razem, gdy operacja usługi jest wywoływana nowa odpowiedź jest buforowana.</span><span class="sxs-lookup"><span data-stu-id="8846e-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="8846e-137">W <`sqlCacheDependency`> element dodać bazy danych i odwołać się do ciągów `databases` połączeń w <> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8846e-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="8846e-138">Następnie należy skonfigurować ustawienia pamięci podręcznej wyjściowej w <`caching`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8846e-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="8846e-139">W tym miejscu czas trwania pamięci `varyByParam` podręcznej jest ustawiony `sqlDependency` na 60 sekund, jest ustawiony na brak i jest ustawiony na listę rozdzielaną średnikami pary nazw/tabel rozdzielonych dwukropkami.</span><span class="sxs-lookup"><span data-stu-id="8846e-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="8846e-140">Po zmianie `MyTable` danych w buforowanej odpowiedzi dla operacji usługi jest usuwany i gdy operacja jest wywoływana nowa odpowiedź jest generowany (przez wywołanie operacji usługi), buforowane i zwracane do klienta.</span><span class="sxs-lookup"><span data-stu-id="8846e-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8846e-141">Aby uzyskać ASP.NET dostęp do bazy danych SQL, należy użyć [narzędzia ASP.NET rejestracji programu SQL Server](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="8846e-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="8846e-142">Ponadto należy zezwolić na dostęp do bazy danych i tabeli odpowiedniego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8846e-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="8846e-143">Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do programu SQL Server z aplikacji sieci Web](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8846e-143">For more information, see [Accessing SQL Server from a Web Application](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="8846e-144">Buforowanie warunkowe http get na podstawie</span><span class="sxs-lookup"><span data-stu-id="8846e-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="8846e-145">W scenariuszach HTTP w sieci Web warunkowe http get jest często używane przez usługi do implementowania inteligentnego buforowania HTTP, jak opisano w [specyfikacji HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span><span class="sxs-lookup"><span data-stu-id="8846e-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="8846e-146">Aby to zrobić, usługa musi ustawić wartość nagłówka ETag w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8846e-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="8846e-147">Należy również sprawdzić If-None-Match nagłówka w żądaniu HTTP, aby zobaczyć, czy którykolwiek z ETag określony pasuje do bieżącego ETag.</span><span class="sxs-lookup"><span data-stu-id="8846e-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="8846e-148">W przypadku żądań <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> GET i HEAD przyjmuje wartość ETag i sprawdza ją względem nagłówka If-None-Match żądania.</span><span class="sxs-lookup"><span data-stu-id="8846e-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="8846e-149">Jeśli nagłówek jest obecny i istnieje <xref:System.ServiceModel.Web.WebFaultException> dopasowanie, a z kodem stanu HTTP 304 (Nie zmodyfikowano) jest generowany i ETag nagłówek jest dodawany do odpowiedzi z pasującym ETag.</span><span class="sxs-lookup"><span data-stu-id="8846e-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="8846e-150">Jedno przeciążenie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody przyjmuje datę ostatniej modyfikacji i sprawdza ją względem nagłówka If-Modified-Since żądania.</span><span class="sxs-lookup"><span data-stu-id="8846e-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="8846e-151">Jeśli nagłówek jest obecny, a zasób nie <xref:System.ServiceModel.Web.WebFaultException> został zmodyfikowany od tego czasu, a z kodem stanu HTTP 304 (Nie zmodyfikowano) jest generowany.</span><span class="sxs-lookup"><span data-stu-id="8846e-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="8846e-152">W przypadku żądań PUT, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> POST i DELETE przyjmuje bieżącą wartość ETag zasobu.</span><span class="sxs-lookup"><span data-stu-id="8846e-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="8846e-153">Jeśli bieżąca wartość ETag jest null, metoda sprawdza, czy If-None- Match nagłówek ma wartość "\*".</span><span class="sxs-lookup"><span data-stu-id="8846e-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="8846e-154">Jeśli bieżąca wartość ETag nie jest wartością domyślną, metoda sprawdza bieżącą wartość ETag względem nagłówka If- Match żądania.</span><span class="sxs-lookup"><span data-stu-id="8846e-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="8846e-155">W obu przypadkach metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> z kodem stanu HTTP 412 (Warunek wstępny nie powiodło się), jeśli oczekiwany nagłówek nie jest obecny w żądaniu lub jego wartość nie spełnia czeku warunkowego i ustawia nagłówek ETag odpowiedzi na bieżącą wartość ETag.</span><span class="sxs-lookup"><span data-stu-id="8846e-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="8846e-156">Zarówno `CheckConditional` metody, <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> jak i metoda zapewnia, że wartość ETag ustawiona w nagłówku odpowiedzi jest prawidłowym etagiem zgodnie ze specyfikacją HTTP.</span><span class="sxs-lookup"><span data-stu-id="8846e-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="8846e-157">Obejmuje to otaczające wartość ETag w cudzysłowach, jeśli nie są one jeszcze obecne i prawidłowo ucieczki żadnych wewnętrznych znaków podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="8846e-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="8846e-158">Słabe porównanie ETag nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="8846e-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="8846e-159">W poniższym przykładzie pokazano, jak używać tych metod.</span><span class="sxs-lookup"><span data-stu-id="8846e-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="8846e-160">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="8846e-160">Security Considerations</span></span>  
 <span data-ttu-id="8846e-161">Żądania, które wymagają autoryzacji nie powinny mieć ich odpowiedzi w pamięci podręcznej, ponieważ autoryzacja nie jest wykonywana, gdy odpowiedź jest obsługiwana z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8846e-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="8846e-162">Buforowanie takich odpowiedzi wprowadziłoby poważną lukę w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="8846e-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="8846e-163">Zazwyczaj żądania, które wymagają autoryzacji zapewniają dane specyficzne dla użytkownika i dlatego buforowanie po stronie serwera nie jest nawet korzystne.</span><span class="sxs-lookup"><span data-stu-id="8846e-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="8846e-164">W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowanie w ogóle będzie bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="8846e-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
