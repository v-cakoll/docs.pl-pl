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
# <a name="caching-support-for-wcf-web-http-services"></a>Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]umożliwia użycie mechanizmu buforowania deklaratywnego już dostępnego w ASP.NET w usługach HTTP w sieci Web WCF. Dzięki temu można buforować odpowiedzi z operacji usługi WCF Web HTTP. Gdy użytkownik wysyła HTTP GET do usługi, która jest skonfigurowana do buforowania, ASP.NET wysyła z powrotem buforowanej odpowiedzi i metoda usługi nie jest wywoływana. Po wygaśnięciu pamięci podręcznej, następnym razem, gdy użytkownik wysyła HTTP GET, metoda usługi jest wywoływana i odpowiedź jest ponownie buforowane. Aby uzyskać więcej informacji na temat ASP.NET buforowania, zobacz [ASP.NET Omówienie buforowania](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
## <a name="basic-web-http-service-caching"></a>Buforowanie podstawowej usługi HTTP w sieci Web  

  Aby włączyć buforowanie usługi HTTP w sieci WEB, należy najpierw włączyć <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET zgodność, stosując ustawienie <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> usługi do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 .NET Framework 4 wprowadza nowy <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atrybut o nazwie, który pozwala określić nazwę profilu pamięci podręcznej. Ten atrybut jest stosowany do operacji usługi. Poniższy przykład stosuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi, aby włączyć zgodność ASP.NET i `GetCustomer` konfiguruje operację buforowania. Atrybut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej, które mają być używane.  
  
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
  
Włącz również tryb zgodności ASP.NET w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Jeśli ASP.NET tryb zgodności nie jest włączony i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używany wyjątek.  
  
 Nazwa profilu pamięci podręcznej określona <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> przez profil pamięci podręcznej, który jest dodawany do pliku konfiguracji Web.config. Profil pamięci podręcznej jest zdefiniowany `outputCacheSetting` w <> element, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 Jest to ten sam element konfiguracji, który jest dostępny dla ASP.NET aplikacji. Aby uzyskać więcej informacji na temat <xref:System.Web.Configuration.OutputCacheProfile>ASP.NET profili pamięci podręcznej, zobacz . W przypadku usług HTTP w sieci Web najważniejsze `cacheDuration` `varyByParam`atrybuty w profilu pamięci podręcznej to: i . Oba te atrybuty są wymagane. `cacheDuration`ustawia czas, przez który odpowiedź powinna być buforowana w ciągu kilku sekund. `varyByParam`umożliwia określenie parametru ciągu zapytania, który jest używany do buforowania odpowiedzi. Wszystkie żądania wykonane z różnymi wartościami parametrów ciągu zapytania są buforowane oddzielnie. Na przykład po pierwszym żądaniu `http://MyServer/MyHttpService/MyOperation?param=10`jest do , wszystkie kolejne żądania wykonane z tym samym identyfikatorem URI zostaną zwrócone buforowanej odpowiedzi (tak długo, jak czas trwania pamięci podręcznej nie upłynął). Odpowiedzi na podobne żądanie, które jest takie samo, ale ma inną wartość dla parametru parametru parametru ciąg zapytania są buforowane oddzielnie. Jeśli nie chcesz tego oddzielnego zachowania `varyByParam` buforowania, ustaw na "none".  
  
## <a name="sql-cache-dependency"></a>Zależność pamięci podręcznej SQL  

  Odpowiedzi na usługi HTTP sieci Web mogą być również buforowane z zależnością pamięci podręcznej SQL. Jeśli usługa WCF Web HTTP zależy od danych przechowywanych w bazie danych SQL, można buforować odpowiedź usługi i unieważnić buforowaną odpowiedź, gdy dane w tabeli bazy danych SQL ulegną zmianie. To zachowanie jest całkowicie skonfigurowane w pliku Web.config. Najpierw zdefiniuj parametry połączenia `connectionStrings` w <> element.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Następnie należy włączyć zależność pamięci podręcznej `caching` SQL w <> element `system.web` w <> element, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 W tym miejscu jest włączona zależność pamięci podręcznej SQL i ustawiony jest czas sondowania 1000 milisekund. Za każdym razem, gdy czas sondowania upływa tabela bazy danych jest sprawdzany pod kątem aktualizacji. Jeśli zostaną wykryte zmiany zawartość pamięci podręcznej są usuwane i następnym razem, gdy operacja usługi jest wywoływana nowa odpowiedź jest buforowana. W <`sqlCacheDependency`> element dodać bazy danych i odwołać się do ciągów `databases` połączeń w <> element, jak pokazano w poniższym przykładzie.  
  
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
  
 Następnie należy skonfigurować ustawienia pamięci podręcznej wyjściowej w <`caching`> element, jak pokazano w poniższym przykładzie.  
  
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
  
 W tym miejscu czas trwania pamięci `varyByParam` podręcznej jest ustawiony `sqlDependency` na 60 sekund, jest ustawiony na brak i jest ustawiony na listę rozdzielaną średnikami pary nazw/tabel rozdzielonych dwukropkami. Po zmianie `MyTable` danych w buforowanej odpowiedzi dla operacji usługi jest usuwany i gdy operacja jest wywoływana nowa odpowiedź jest generowany (przez wywołanie operacji usługi), buforowane i zwracane do klienta.  
  
> [!IMPORTANT]
> Aby uzyskać ASP.NET dostęp do bazy danych SQL, należy użyć [narzędzia ASP.NET rejestracji programu SQL Server](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)). Ponadto należy zezwolić na dostęp do bazy danych i tabeli odpowiedniego konta użytkownika. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do programu SQL Server z aplikacji sieci Web](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).  
  
## <a name="conditional-http-get-based-caching"></a>Buforowanie warunkowe http get na podstawie  

  W scenariuszach HTTP w sieci Web warunkowe http get jest często używane przez usługi do implementowania inteligentnego buforowania HTTP, jak opisano w [specyfikacji HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html). Aby to zrobić, usługa musi ustawić wartość nagłówka ETag w odpowiedzi HTTP. Należy również sprawdzić If-None-Match nagłówka w żądaniu HTTP, aby zobaczyć, czy którykolwiek z ETag określony pasuje do bieżącego ETag.  
  
 W przypadku żądań <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> GET i HEAD przyjmuje wartość ETag i sprawdza ją względem nagłówka If-None-Match żądania. Jeśli nagłówek jest obecny i istnieje <xref:System.ServiceModel.Web.WebFaultException> dopasowanie, a z kodem stanu HTTP 304 (Nie zmodyfikowano) jest generowany i ETag nagłówek jest dodawany do odpowiedzi z pasującym ETag.  
  
 Jedno przeciążenie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody przyjmuje datę ostatniej modyfikacji i sprawdza ją względem nagłówka If-Modified-Since żądania. Jeśli nagłówek jest obecny, a zasób nie <xref:System.ServiceModel.Web.WebFaultException> został zmodyfikowany od tego czasu, a z kodem stanu HTTP 304 (Nie zmodyfikowano) jest generowany.  
  
 W przypadku żądań PUT, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> POST i DELETE przyjmuje bieżącą wartość ETag zasobu. Jeśli bieżąca wartość ETag jest null, metoda sprawdza, czy If-None- Match nagłówek ma wartość "*".  Jeśli bieżąca wartość ETag nie jest wartością domyślną, metoda sprawdza bieżącą wartość ETag względem nagłówka If- Match żądania. W obu przypadkach metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> z kodem stanu HTTP 412 (Warunek wstępny nie powiodło się), jeśli oczekiwany nagłówek nie jest obecny w żądaniu lub jego wartość nie spełnia czeku warunkowego i ustawia nagłówek ETag odpowiedzi na bieżącą wartość ETag.  
  
 Zarówno `CheckConditional` metody, <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> jak i metoda zapewnia, że wartość ETag ustawiona w nagłówku odpowiedzi jest prawidłowym etagiem zgodnie ze specyfikacją HTTP. Obejmuje to otaczające wartość ETag w cudzysłowach, jeśli nie są one jeszcze obecne i prawidłowo ucieczki żadnych wewnętrznych znaków podwójnego cudzysłowu. Słabe porównanie ETag nie jest obsługiwane.  
  
 W poniższym przykładzie pokazano, jak używać tych metod.  
  
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
  
## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 Żądania, które wymagają autoryzacji nie powinny mieć ich odpowiedzi w pamięci podręcznej, ponieważ autoryzacja nie jest wykonywana, gdy odpowiedź jest obsługiwana z pamięci podręcznej.  Buforowanie takich odpowiedzi wprowadziłoby poważną lukę w zabezpieczeniach.  Zazwyczaj żądania, które wymagają autoryzacji zapewniają dane specyficzne dla użytkownika i dlatego buforowanie po stronie serwera nie jest nawet korzystne.  W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowanie w ogóle będzie bardziej odpowiednie.
