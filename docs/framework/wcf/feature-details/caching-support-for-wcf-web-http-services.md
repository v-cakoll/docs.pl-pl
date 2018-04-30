---
title: Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cffa0e1c18fd3e1207b40c699684ebaa49511384
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="caching-support-for-wcf-web-http-services"></a>Obsługa buforowania dla opartych na protokole HTTP usług sieci Web programu WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Umożliwia korzystanie z deklaratywne mechanizm buforowania już dostępne w programie ASP.NET w usługach WCF Web HTTP. Dzięki temu można do pamięci podręcznej odpowiedzi z operacji usługi WCF Web HTTP. Gdy użytkownik wysyła do usługi, który jest skonfigurowany dla buforowania GET protokołu HTTP, ASP.NET odsyła odpowiedź buforowana i nie wywołano metody usługi. Po wygaśnięciu pamięci podręcznej, przy następnym użytkownik wysyła HTTP GET, jest wywoływana przez metodę usługi i ponownie buforowaną odpowiedź. Aby uzyskać więcej informacji na temat buforowania platformy ASP.NET, zobacz [omówienie pamięci podręcznej programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Usługa HTTP sieci Web podstawowe buforowanie  
 Aby włączyć protokół HTTP sieci WEB usługi buforowania, należy najpierw włączyć zgodności z platformą ASP.NET, stosując <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do ustawienia usługi <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> do <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> lub <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] wprowadzono nowy atrybut o nazwie <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> który pozwala określić nazwę profilu pamięci podręcznej. Ten atrybut jest stosowany do operacji usługi. Następujący przykład dotyczy <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do usługi w celu włączenia zgodności z platformą ASP.NET i konfiguruje `GetCustomer` operacji do buforowania. <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atrybut określa profil pamięci podręcznej, który zawiera ustawienia pamięci podręcznej do użycia.  
  
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
>  Jeśli nie włączono tryb zgodności ASP.NET i <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> jest używany jest zgłaszany wyjątek.  
  
 Nazwa profilu pamięci podręcznej, określony przez <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identyfikuje profil pamięci podręcznej, który jest dodawany do pliku konfiguracji Web.config. Profil pamięci podręcznej jest zdefiniowana z w <`outputCacheSetting`> element, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 Jest to tego samego elementu konfiguracji, która jest dostępna dla aplikacji ASP.NET. Aby uzyskać więcej informacji na temat profilów pamięci podręcznej programu ASP.NET, zobacz <xref:System.Web.Configuration.OutputCacheProfile>. Dla usług HTTP sieci Web, są najważniejsze atrybuty w profilu pamięci podręcznej: `cacheDuration` i `varyByParam`. Oba te atrybuty są wymagane. `cacheDuration` Ustawia czas, które mają być buforowane odpowiedzi w sekundach. `varyByParam` można określić parametr ciągu zapytania używanego do odpowiedzi z pamięci podręcznej. Wszystkie żądania z wartościami parametrów ciągu zapytania różnych są buforowane oddzielnie. Na przykład po wysłaniu żądania początkowego do http://MyServer/MyHttpService/MyOperation?param=10 wszystkie kolejne żądania o tym samym identyfikatorze URI będzie zwracany buforowanej odpowiedzi (o ile nie upłynął czas trwania pamięci podręcznej). Odpowiedzi na żądania podobne jest taki sam, ale ma inną wartość dla parametru ciągu zapytania parametru są buforowane oddzielnie. Jeśli nie chcesz, aby to zachowanie buforowania w oddzielnych, ustaw `varyByParam` "none".  
  
## <a name="sql-cache-dependency"></a>Zależności bufora SQL  
 Odpowiedzi usługi HTTP sieci Web można buforować w taki sposób, w zależności buforu SQL. Jeśli usługi WCF Web HTTP zależy od danych przechowywanych w bazie danych SQL, można buforować odpowiedzi usługi akcji i unieważnić buforowanej odpowiedzi podczas zmiany tabeli bazy danych SQL danych. To zachowanie jest całkowicie skonfigurowany w pliku Web.config. Należy określić parametry połączenia w <`connectionStrings`> elementu.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Następnie należy włączyć zależność buforu SQL w ramach <`caching`> w elemencie <`system.web`> element, jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 W tym miejscu zależności bufora SQL jest włączona i godzina sondowania, 1000 milisekund jest ustawiona. Zawsze sondowania upłynie tabeli bazy danych jest sprawdzany pod kątem aktualizacji. Jeśli zostaną wykryte zmiany zawartość pamięci podręcznej są usuwane i przy następnej operacji usługi jest wywoływany nowej odpowiedzi są buforowane. W ramach <`sqlCacheDependency`> element Dodaj bazy danych i referencyjne parametry połączenia w <`databases`> element, jak pokazano w poniższym przykładzie.  
  
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
  
 Następnie należy skonfigurować ustawienia wyjściowej pamięci podręcznej w <`caching`> element, jak pokazano w poniższym przykładzie.  
  
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
  
 W tym miejscu czas buforowania ma ustawioną wartość 60 sekund, `varyByParam` ma wartość none i `sqlDependency` ma ustawioną wartość listy rozdzielanych średnikami oddzielone dwukropkiem pary nazwa/tabeli bazy danych. Gdy dane w `MyTable` zostanie zmieniona buforowanej odpowiedzi dla operacji usługi zostanie usunięty i po wywołaniu operacji nową odpowiedź jest generowany (przez wywołanie operacji usługi), w pamięci podręcznej i zwracany do klienta.  
  
> [!IMPORTANT]
>  Dla platformy ASP.NET dostępu do bazy danych SQL, należy użyć [ASP.NET SQL Server Registration Tool](http://go.microsoft.com/fwlink/?LinkId=152536). Ponadto musisz zezwolić na odpowiedniego użytkownika konta dostępu do bazy danych i tabeli. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do programu SQL Server z aplikacji sieci Web](http://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Warunkowe HTTP GET na podstawie buforowanie  
 W scenariuszach protokołu HTTP sieci Web warunkowego HTTP GET jest często używane przez usługi do zaimplementowania inteligentne buforowanie HTTP zgodnie z opisem w [specyfikacji HTTP](http://go.microsoft.com/fwlink/?LinkId=165800). W tym celu usługi należy ustawić wartość nagłówka ETag w odpowiedzi HTTP. On również sprawdzić nagłówka If-None-Match w żądaniu HTTP, czy dowolne ETag określony odpowiada bieżącej ETag.  
  
 Dla żądania GET i HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> przyjmuje wartość ETag i porównuje ją z nagłówka If-None-Match żądania. Jeśli istnieje nagłówek i są zgodne, <xref:System.ServiceModel.Web.WebFaultException> protokołu HTTP jest generowany kod stanu 304 (nie jest modyfikowany) i dodaniu nagłówka ETag do odpowiedzi z pasującego tagu ETag.  
  
 Jednego przeciążenia <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda pobiera daty ostatniej modyfikacji i porównuje ją z nagłówka If-Modified-Since żądania. Jeśli istnieje nagłówek i zasób nie został zmodyfikowany od czasu, <xref:System.ServiceModel.Web.WebFaultException> protokołu HTTP jest generowany kod stanu 304 (nie jest modyfikowany).  
  
 Dla żądania PUT, POST i DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> przejście do bieżącej wartości ETag dla zasobu. Jeśli do bieżącej wartości ETag ma wartość null, metoda sprawdza, czy nagłówek If-None-Match ma wartość "*".  Jeśli do bieżącej wartości ETag nie jest wartością domyślną, metoda sprawdza do bieżącej wartości ETag dla nagłówka If - Match żądania. W obu przypadkach metoda zgłasza <xref:System.ServiceModel.Web.WebFaultException> ze stanem HTTP code oczekiwano nagłówka nie znajduje się w żądaniu lub jego wartość nie spełnia warunkowego sprawdzenia i ustawia nagłówek ETag odpowiedzi do bieżącego tagu ETag 412 (warunek wstępny nie powiodła się.) wartość.  
  
 Zarówno `CheckConditional` metod i <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> — metoda gwarantuje, że wartość ETag w nagłówku odpowiedzi jest prawidłowy element ETag według specyfikacji HTTP. Obejmuje to otaczającego wartość ETag w podwójne cudzysłowy, jeśli nie istnieją już i poprawnie anulowanie znaków podwójnego cudzysłowu wewnętrznego. Słaby element ETag porównania nie jest obsługiwane.  
  
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
 Żądania, które wymagają autoryzacji nie powinna mieć odpowiedzi pamięci podręcznej, autoryzacji nie jest wykonywana po udostępnieniu odpowiedzi z pamięci podręcznej.  Buforowanie odpowiedzi na takie spowodowałoby to powstanie luki w zabezpieczeniach poważne.  Zazwyczaj żądania, które wymagają autoryzacji zawierają dane specyficzne dla użytkownika i dlatego buforowanie po stronie serwera nie jest jeszcze korzystne.  W takich sytuacjach buforowanie po stronie klienta lub po prostu nie buforowanie na wszystkich będą bardziej odpowiednie.
