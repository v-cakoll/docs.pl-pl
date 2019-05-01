---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 6c601b19a0b3b9b3eddbd686c316ce7e2cdf7778
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857665"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Umożliwia użycie deklaratywne mechanizm buforowania, dostępnych w programie ASP.NET w usługach WCF Web HTTP. Dzięki temu można buforowanie odpowiedzi z operacji usługi WCF Web HTTP. Gdy użytkownik wysyła żądania HTTP GET do usługi, który jest skonfigurowany do buforowania, ASP.NET odsyła odpowiedzi z pamięci podręcznej i nie jest wywoływana metoda usługi. Po wygaśnięciu pamięci podręcznej, następnym razem użytkownik wysyła żądania HTTP GET, wywoływana jest metoda swoje usługi i odpowiedź jest zbuforowana z jeszcze raz. Aby uzyskać więcej informacji na temat buforowania platformy ASP.NET, zobacz [omówienie buforowania programu ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Usługa HTTP Basic Web buforowania  
 Aby włączyć protokół HTTP sieci WEB usługi pamięci podręcznej, należy najpierw włączyć zgodność platformy ASP.NET, stosując <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do ustawienia usługi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] wprowadza nowy atrybut o nazwie <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pozwala określić nazwę profilu pamięci podręcznej. Ten atrybut jest stosowany do operacji usługi. Następujący przykład dotyczy <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi, aby włączyć zgodności z platformą ASP.NET i konfiguruje `GetCustomer` operacji do buforowania. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Atrybut określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej, który ma być używany.  
  
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
  
 Należy również włączyć tryb zgodności ASP.NET w pliku Web.config, jak pokazano w poniższym przykładzie.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  Jeśli tryb zgodności ASP.NET nie jest włączona i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używana jest zgłaszany wyjątek.  
  
 Nazwa profilu pamięci podręcznej, które są określone przez <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identyfikuje profil pamięci podręcznej, który jest dodawany do pliku konfiguracji Web.config. Profil pamięci podręcznej jest zdefiniowana za pomocą w <`outputCacheSetting`> elementu, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 Jest to ten sam element konfiguracji, która jest dostępna dla aplikacji ASP.NET. Aby uzyskać więcej informacji na temat profilów w pamięci podręcznej programu ASP.NET, zobacz <xref:System.Web.Configuration.OutputCacheProfile>. Dla usług HTTP w sieci Web są najważniejsze atrybutów w pamięci podręcznej profilu: `cacheDuration` i `varyByParam`. Te atrybuty są wymagane. `cacheDuration` Określa ilość czasu, które mają być buforowane odpowiedzi w ciągu kilku sekund. `varyByParam` Pozwala określić parametr ciągu zapytania używanego do buforowanie odpowiedzi. Wszystkie żądania przekazywane za inne wartości parametrów ciągów są buforowane osobno. Na przykład, po nawiązaniu początkowego żądania do `http://MyServer/MyHttpService/MyOperation?param=10`, wszystkie kolejne żądania z tego samego identyfikatora URI zostałyby zwrócone w odpowiedzi z pamięci podręcznej (, dopóki nie upłynie czas trwania pamięci podręcznej). Odpowiedzi dla podobne żądania, która jest taka sama, ale ma inną wartość dla parametru ciągu zapytania parametr są buforowane osobno. Jeśli nie mają oddzielne zachowania buforowania, ustaw `varyByParam` na "none".  
  
## <a name="sql-cache-dependency"></a>Zależności pamięci podręcznej SQL  
 Odpowiedzi usługi HTTP sieci Web można buforować w taki sposób, w przypadku zależności pamięci podręcznej SQL. Jeśli usługi WCF Web HTTP jest zależna od danych przechowywanych w bazie danych SQL, można buforować odpowiedzi usługi i unieważnić buforowaną odpowiedź, gdy danych w SQL bazy danych zmian w tabeli. To zachowanie jest całkowicie skonfigurowany w pliku Web.config. Należy określić ciąg połączenia w <`connectionStrings`> element.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Następnie należy włączyć zależności pamięci podręcznej SQL w ramach <`caching`> elemencie <`system.web`> elementu, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 W tym miejscu zależności pamięci podręcznej SQL jest włączona i ustawiono czas sondowania 1000 milisekund. Każdorazowo podczas sondowania upływa tabeli bazy danych jest sprawdzane pod kątem aktualizacji. Jeśli wykryto zmiany zawartości pamięci podręcznej są usuwane, a przy następnej operacji usługi jest wywoływany nowej odpowiedzi są buforowane. W ramach <`sqlCacheDependency`> elementu Dodawanie baz danych i odwoływać się do parametrów połączenia w ramach <`databases`> elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 Następnie należy skonfigurować ustawienia wyjściowej pamięci podręcznej w ramach <`caching`> elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 W tym miejscu czas trwania pamięci podręcznej jest ustawiona na 60 sekund, `varyByParam` jest ustawiona na wartość none i `sqlDependency` ustawiono rozdzielaną średnikami listę par nazwa/table bazy danych, rozdzielone średnikami. Gdy dane w `MyTable` zostanie zmieniony buforowane odpowiedzi dla operacji usługi zostanie usunięty, a podczas wywoływania operacji nowej odpowiedzi wygenerowanych (według wywoływanie operacji usługi), pamięci podręcznej i zwracany do klienta.  
  
> [!IMPORTANT]
>  W technologii ASP.NET dostępu do bazy danych SQL, należy użyć [narzędzia rejestracji serwera SQL platformy ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152536). Ponadto muszą zezwalać na do odpowiedniego dostępu do bazy danych i tabeli. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do programu SQL Server z aplikacji sieci Web](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Warunkowe UZYSKAĆ oparty na protokole HTTP buforowania  
 W scenariuszach protokołu HTTP sieci Web warunkowego HTTP GET jest często używana przez usługi do zaimplementowania buforowania inteligentnego HTTP, zgodnie z opisem w [specyfikację protokołu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). W tym celu usługa należy ustawić wartość nagłówka ETag w odpowiedzi HTTP. On także sprawdzić nagłówek If-None-Match w żądaniu HTTP, aby sprawdzić, czy dowolny element ETag określony odpowiada bieżący element ETag.  
  
 W przypadku żądań GET i HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje wartość elementu ETag i porównuje ją z nagłówka If-None-Match żądania. Nagłówek jest obecny, jeśli ma dopasowania <xref:System.ServiceModel.Web.WebFaultException> za pośrednictwem protokołu HTTP jest generowany kod stanu 304 (nie zmodyfikowano), a nagłówka ETag jest dodawany do odpowiedzi z pasującego tagu ETag.  
  
 Jednego przeciążenia <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda przyjmuje daty ostatniej modyfikacji i porównuje ją z nagłówka If-Modified-Since żądania. Jeśli nagłówek a zasób nie został zmodyfikowany od czasu, <xref:System.ServiceModel.Web.WebFaultException> za pośrednictwem protokołu HTTP jest generowany kod stanu 304 (nie zmodyfikowano).  
  
 Dla żądania PUT, POST i DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> przyjmuje bieżącej wartości zasobu element ETag. Jeśli bieżąca wartość elementu ETag ma wartość null, metoda sprawdza, czy nagłówek If-None-Match ma wartość "*".  Jeśli bieżąca wartość elementu ETag nie jest wartość domyślna, metoda sprawdza bieżącą wartość elementu ETag dla nagłówka If - Match żądania. W obu przypadkach, metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> ze stanem HTTP kodu oczekiwano nagłówka nie znajduje się w żądaniu lub jego wartość nie spełnia warunkowego wyboru i ustawia dla nagłówka ETag odpowiedzi na bieżący element ETag 412 (niepowodzenie warunku wstępnego) wartość.  
  
 Zarówno `CheckConditional` metod i <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda gwarantuje, że wartość elementu ETag w nagłówku odpowiedzi jest prawidłowy element ETag zgodnie ze specyfikacją protokołu HTTP. Obejmuje to otaczające wartość elementu ETag w cudzysłów, jeśli nie są jeszcze obecne i prawidłowo anulowania zapewnianego element znaków wewnętrznego podwójnego cudzysłowu. Słabe porównania element ETag nie jest obsługiwane.  
  
 Poniższy przykład przedstawia sposób użycia tych metod.  
  
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
 Żądania, które wymagają autoryzacji nie powinny mieć ich odpowiedzi w pamięci podręcznej, ponieważ autoryzacji nie jest przeprowadzane, gdy odpowiedź jest obsługiwany z pamięci podręcznej.  Buforowanie odpowiedzi na takie spowodowałoby to powstanie luk w zabezpieczeniach z powodu poważnego naruszenia zabezpieczeń.  Zazwyczaj żądania, które wymagają autoryzacji dostarczać dane specyficzne dla użytkownika, i w związku z tym buforowanie po stronie serwera nie jest nawet korzystne.  W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowania w ogóle będzie bardziej odpowiednie.
