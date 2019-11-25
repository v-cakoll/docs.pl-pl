---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 7c60deab635c29785398a1b50f9cf14c0f688420
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141787"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] umożliwia korzystanie z mechanizmu deklaracyjnej pamięci podręcznej, który jest już dostępny w ASP.NET w usługach HTTP sieci Web WCF. Pozwala to na buforowanie odpowiedzi z operacji usługi HTTP sieci Web w programie WCF. Gdy użytkownik wysyła HTTP GET do usługi skonfigurowanej do buforowania, ASP.NET wysyła do tyłu buforowaną odpowiedź i metoda usługi nie jest wywoływana. Gdy pamięć podręczna zostanie wygaśnie, następnym razem, gdy użytkownik wyśle HTTP GET, wywoływana jest metoda usługi i odpowiedź jest ponownie buforowana. Aby uzyskać więcej informacji o pamięci podręcznej ASP.NET, zobacz [buforowanie ASP.NET — Omówienie](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Podstawowe buforowanie usługi HTTP w sieci Web  
 Aby włączyć buforowanie usługi HTTP w sieci WEB, należy najpierw włączyć zgodność ASP.NET, stosując <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do ustawienia usługi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 .NET Framework 4 wprowadza nowy atrybut o nazwie <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, który umożliwia określenie nazwy profilu pamięci podręcznej. Ten atrybut jest stosowany do operacji usługi. W poniższym przykładzie zastosowano <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi, aby włączyć zgodność ASP.NET i skonfigurować operację `GetCustomer` dla buforowania. Atrybut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej, które mają być używane.  
  
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
  
 Należy również włączyć tryb zgodności ASP.NET w pliku Web. config, jak pokazano w poniższym przykładzie.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Jeśli tryb zgodności ASP.NET nie jest włączony, a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używany wyjątek jest zgłaszany.  
  
 Nazwa profilu pamięci podręcznej określona przez <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identyfikuje profil pamięci podręcznej, który jest dodawany do pliku konfiguracyjnego Web. config. Profil pamięci podręcznej jest zdefiniowany za pomocą w <`outputCacheSetting`> elementu, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 Jest to ten sam element konfiguracji, który jest dostępny dla aplikacji ASP.NET. Aby uzyskać więcej informacji na temat profili pamięci podręcznej ASP.NET, zobacz <xref:System.Web.Configuration.OutputCacheProfile>. W przypadku usług HTTP w sieci Web najważniejsze atrybuty w profilu pamięci podręcznej to: `cacheDuration` i `varyByParam`. Oba te atrybuty są wymagane. `cacheDuration` określa, ile czasu odpowiedź powinna być buforowana w sekundach. `varyByParam` pozwala określić parametr ciągu zapytania, który jest używany do buforowania odpowiedzi. Wszystkie żądania z różnymi wartościami parametrów ciągu zapytania są buforowane osobno. Na przykład po wprowadzeniu pierwszego żądania do `http://MyServer/MyHttpService/MyOperation?param=10`wszystkie kolejne żądania wykonane przy użyciu tego samego identyfikatora URI zostałyby zwrócone w pamięci podręcznej (o ile nie upłynął czas trwania pamięci podręcznej). Odpowiedzi dla podobnego żądania, które jest takie samo, ale ma inną wartość dla parametru ciągu zapytania parametru są buforowane osobno. Jeśli nie chcesz, aby to oddzielne zachowanie buforowania, ustaw dla `varyByParam` wartość "Brak".  
  
## <a name="sql-cache-dependency"></a>Zależność pamięci podręcznej SQL  
 Odpowiedzi usługi HTTP sieci Web mogą być również buforowane z zależnością pamięci podręcznej SQL. Jeśli usługa HTTP sieci Web w programie WCF zależy od danych przechowywanych w bazie danych SQL, może być konieczne przechowanie odpowiedzi usługi i unieważnienie pamięci podręcznej w przypadku zmiany danych w tabeli bazy danych SQL. To zachowanie jest konfigurowane w całości w pliku Web. config. Najpierw należy zdefiniować parametry połączenia w elemencie <`connectionStrings`>.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Następnie należy włączyć zależność pamięci podręcznej SQL w <`caching`> elementu w ramach <`system.web`>, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 W tym miejscu jest włączona zależność pamięci podręcznej SQL i ustawiono czas sondowania 1000 milisekund. Za każdym razem, gdy upłynie czas sondowania tabela bazy danych jest sprawdzana pod kątem aktualizacji. W przypadku wykrycia zmian zawartość pamięci podręcznej jest usuwana, a przy następnym wywołaniu operacji usługi jest buforowana Nowa odpowiedź. W`sqlCacheDependency`< element > dodać bazy danych i odwołać się do parametrów połączenia w elemencie <`databases`>, jak pokazano w poniższym przykładzie.  
  
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
  
 Następnie należy skonfigurować ustawienia wyjściowej pamięci podręcznej w <`caching`> elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 W tym miejscu czas trwania pamięci podręcznej jest ustawiony na 60 sekund, `varyByParam` jest ustawiona na None, a `sqlDependency` jest ustawiona na listę rozdzielaną średnikami nazw bazy danych/tabel oddzielonych średnikami. W przypadku zmiany danych w `MyTable` buforowana odpowiedź dla operacji usługi jest usuwana, a po wywołaniu operacji jest generowana Nowa odpowiedź (przez wywołanie operacji usługi), w pamięci podręcznej i zwróconej do klienta.  
  
> [!IMPORTANT]
> Aby ASP.NET uzyskać dostęp do bazy danych SQL, należy użyć [narzędzia rejestracji SQL Server ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152536). Ponadto należy zezwolić na dostęp odpowiednich kont użytkowników do bazy danych i tabeli. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do SQL Server z aplikacji sieci Web](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Buforowanie warunkowe oparte na protokole HTTP  
 W scenariuszach HTTP sieci Web warunkowe pobieranie HTTP jest często używane przez usługi do implementowania inteligentnego buforowania HTTP zgodnie z opisem w [specyfikacji protokołu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). Aby to zrobić, usługa musi ustawić wartość nagłówka ETag w odpowiedzi HTTP. Należy również sprawdzić nagłówek If-None-Match w żądaniu HTTP, aby sprawdzić, czy którykolwiek z określonych elementów ETag jest zgodny z bieżącym elementem ETag.  
  
 W przypadku żądań GET i Web<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje wartość ETag i sprawdza ją w nagłówku If-None-Match żądania. Jeśli nagłówek jest obecny i istnieje dopasowanie, <xref:System.ServiceModel.Web.WebFaultException> z kodem stanu HTTP 304 (nie zmodyfikowany) i zostanie dodany nagłówek ETag do odpowiedzi z pasującym elementem ETag.  
  
 Jedno Przeciążenie metody <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje datę ostatniej modyfikacji i sprawdza ją względem nagłówka If-Modified-od żądania. Jeśli nagłówek jest obecny, a zasób nie został zmodyfikowany od czasu, zostanie zgłoszony <xref:System.ServiceModel.Web.WebFaultException> z kodem stanu HTTP 304 (niezmodyfikowanym).  
  
 W przypadku żądań PUT, POST i DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> pobiera bieżącą wartość ETag zasobu. Jeśli bieżąca wartość ETag ma wartość null, Metoda sprawdza, czy nagłówek If-None-Match ma wartość "*".  Jeśli bieżąca wartość ETag nie jest wartością domyślną, Metoda sprawdza bieżącą wartość ETag w nagłówku If-Match żądania. W obu przypadkach Metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> przy użyciu kodu stanu HTTP 412 (warunki wstępne nie powiodło się), jeśli oczekiwany nagłówek nie występuje w żądaniu lub jego wartość nie spełnia warunkowego sprawdzania i ustawia nagłówek ETag odpowiedzi na bieżącą wartość ETag.  
  
 Zarówno metody `CheckConditional`, jak i Metoda <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> zapewniają, że wartość ETag ustawiona w nagłówku odpowiedzi jest prawidłowym elementem ETag zgodnie ze specyfikacją protokołu HTTP. Obejmuje to otaczającie wartości ETag w podwójnych cudzysłowach, jeśli nie są one jeszcze obecne i prawidłowo ucieczką znaków wewnętrznego cudzysłowu. Słabe porównanie ETag nie jest obsługiwane.  
  
 Poniższy przykład pokazuje, jak używać tych metod.  
  
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
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Żądania, które wymagają autoryzacji, nie powinny mieć buforowanych odpowiedzi, ponieważ autoryzacja nie jest wykonywana, gdy odpowiedź jest obsługiwana z pamięci podręcznej.  Buforowanie takich odpowiedzi spowoduje powstanie poważnych luk w zabezpieczeniach.  Zazwyczaj żądania, które wymagają autoryzacji, zapewniają dane specyficzne dla użytkownika i dlatego buforowanie po stronie serwera nie jest jeszcze korzystne.  W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowanie w ogóle będzie bardziej odpowiednie.
