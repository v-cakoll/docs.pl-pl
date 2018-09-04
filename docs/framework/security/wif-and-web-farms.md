---
title: Program WIF i farmy serwerów sieci Web
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 365416a82881c32b8fdcd3211aa42acb9f273483
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502732"
---
# <a name="wif-and-web-farms"></a>Program WIF i farmy serwerów sieci Web
Korzystając z programu Windows Identity Foundation (WIF) można zabezpieczyć zasobów jednostki uzależnionej aplikacji innych firm (RP), które zostało wdrożone w ramach farmy sieci web, należy wykonać określone kroki, aby upewnić się, że program WIF może przetwarzać tokenów z wystąpień aplikacji jednostki Uzależnionej, uruchomione na różnych komputery z farmy. Proces przetwarzania obejmuje sprawdzanie podpisów tokenów sesji, szyfrowania i odszyfrowywania tokenów sesji, buforowanie tokenów sesji i wykrywanie powtórzone tokenów zabezpieczających.  
  
 W typowych przypadkach stosowania programu WIF do zabezpieczania zasobów aplikacji jednostki Uzależnionej — czy punktu przywracania jest uruchomiona na tym samym komputerze lub w ramach farmy sieci web — ustanowiono połączenie z klientem, oparte na token zabezpieczający, który został uzyskany z usługi tokenu zabezpieczającego (STS). Pozwoli to uniknąć, wymuszając od klienta do uwierzytelniania w STS dla każdego zasobu aplikacji, która jest zabezpieczony za pomocą programu WIF. Aby uzyskać więcej informacji na temat obsługi sesjami programu WIF, zobacz [Zarządzanie sesjami programu WIF](../../../docs/framework/security/wif-session-management.md).  
  
 Gdy używane są ustawienia domyślne, program WIF wykonuje następujące czynności:  
  
-   Używa wystąpienia <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy na odczytywanie i zapisywanie tokenu sesji (wystąpienie <xref:System.IdentityModel.Tokens.SessionSecurityToken> klasy), niesie ze sobą oświadczenia i inne informacje o tokenie zabezpieczającym, który był używany do uwierzytelniania, a także informacje o sesji samego siebie. Token sesji jest spakowany i przechowywane w pliku cookie sesji. Domyślnie <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> używa <xref:System.IdentityModel.ProtectedDataCookieTransform> klasy, która korzysta z interfejsu API ochrony danych (DPAPI), aby chronić tokenu sesji. DPAPI zapewnia ochronę przy użyciu poświadczeń użytkownika lub komputera i zapisuje dane klucza w profilu użytkownika.  
  
-   Używa domyślnie, implementacja w pamięci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy w celu przechowywania i przetwarzania tokenu sesji.  
  
 Te domyślne ustawienia działają w scenariuszach, w których wdrożono aplikację jednostki Uzależnionej na jednym komputerze. Jednak po wdrożeniu w ramach farmy sieci web, każde żądanie HTTP może być wysyłane do i przetworzone przez inne wystąpienie aplikacji jednostki Uzależnionej uruchomiony na innym komputerze. Domyślne ustawienia programu WIF opisanych powyżej w tym scenariuszu nie będą działać, ponieważ token ochrony i buforowaniem tokena są zależne od określonego komputera.  
  
 Aby wdrożyć aplikację jednostki Uzależnionej w ramach farmy sieci web, upewnij się, że przetwarzania tokenów, sesji (a także powtórzonym tokenów) nie jest zależny od aplikacja była uruchomiona na określonym komputerze. Jednym ze sposobów, aby zrobić to do wdrożenia aplikacji jednostki Uzależnionej, tak aby używał funkcje udostępniane przez platformę ASP.NET `<machineKey>` element konfiguracji i udostępnia funkcję buforowania rozproszonego przetwarzania tokenów sesji i odtwarzany tokenów. `<machineKey>` Element umożliwia określenie kluczy wymaganych do weryfikacji, szyfrowania i odszyfrowywania tokenów w pliku konfiguracji, który pozwala na określenie tych samych kluczy na różnych komputerach w farmie internetowej. Program WIF oferuje specjalne sesji programu obsługi tokenów, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, która chroni tokeny przy użyciu kluczy, określone w `<machineKey>` elementu. Aby zaimplementować tę strategię, należy przestrzegać następujących zasad:  
  
-   Za pomocą programu ASP.NET `<machineKey>` element konfiguracji, aby jawnie określić kluczy podpisywania i szyfrowania, które mogą być używane na komputerach w farmie. Następujący kody XML pokazuje specyfikację `<machineKey>` pod `<system.web>` elementu w pliku konfiguracji.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Konfigurowanie aplikacji do korzystania z <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> , dodając ją do kolekcji programu obsługi tokenów. Należy najpierw usunąć <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (lub dowolnej procedury obsługi pochodzący od <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy) z kolekcji programu obsługi tokenów, jeśli program obsługi jest obecny. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Używa <xref:System.IdentityModel.Services.MachineKeyTransform> klasy, która chroni dane pliku cookie sesji przy użyciu materiałami kryptograficznymi określone w `<machineKey>` elementu. Następujący kody XML pokazuje sposób dodawania <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> do kolekcji programu obsługi tokenów.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Pochodzi od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> i implementowanie rozproszonej pamięci podręcznej, oznacza to, że pamięć podręczna, która jest dostępna ze wszystkich komputerów w farmie serwerów, na którym mogą zostać uruchomione jednostki Uzależnionej. Konfigurowanie jednostki Uzależnionej do określania za pomocą rozproszonej pamięci podręcznej [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) elementu w pliku konfiguracji. Można zastąpić <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metodę w pochodnej klasie do zaimplementowania elementów podrzędnych `<sessionSecurityTokenCache>` elementu, jeśli są one wymagane.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Jednym ze sposobów implementuje się buforowanie rozproszonej jest zapewnienie WCF frontonu dla swojej niestandardowej pamięci podręcznej. Aby uzyskać więcej informacji na temat implementowania WCF z pamięci podręcznej usługi zobacz [usługi pamięć podręczna WCF](#BKMK_TheWCFCachingService). Aby uzyskać więcej informacji o implementowaniu klienta WCF, który aplikacja jednostki Uzależnionej można użyć do wywołania usługi buforowania, zobacz [WCF buforowania klient](#BKMK_TheWCFClient).  
  
-   Jeśli aplikacja wykryje powtórzonym tokeny należy wykonać podobne rozproszonej pamięci podręcznej strategii dla pamięci podręcznej powtórzeń tokenów, wynikające z <xref:System.IdentityModel.Tokens.TokenReplayCache> i wskazanie swoje powtarzania tokenu buforowania usługi w [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element konfiguracji.  
  
> [!IMPORTANT]
>  Przykładowy kod XML i kodu, w tym temacie są pobierane z [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) próbki.  
  
> [!IMPORTANT]
>  Przykłady w tym temacie podano jako — jest i nie są przeznaczone do użycia w kodzie produkcyjnym bez żadnych modyfikacji.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Usługa pamięć podręczna WCF  
 Następujący interfejs definiuje kontrakt między buforowania usługi WCF i klienta WCF, używany przez aplikację jednostki uzależnionej do komunikowania się z nim. Zasadniczo udostępnia metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy jako operacji usługi.  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 Poniższy kod przedstawia implementację WCF usługi buforowania. W tym przykładzie, domyślnie jest używany implementowany przez program WIF pamięci podręcznej tokenu sesji w pamięci. Alternatywnie można zaimplementować trwałość pamięci podręcznej, wspierana przez bazę danych. `ISessionSecurityTokenCacheService` definiuje interfejs przedstawionych powyżej. W tym przykładzie nie wszystkie metody, trzeba do zaimplementowania interfejsu są wyświetlane dla skrócenia programu.  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a>Pamięć podręczna klienta platformy WCF  
 W tej sekcji przedstawiono implementację klasy, która pochodzi od klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> i że delegaty usługę buforowania. Konfigurowanie aplikacji jednostki Uzależnionej, aby użyć tej klasy przy użyciu [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) elementu, tak jak następujący kod XML  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Przesłonięć klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodę, aby uzyskać punkt końcowy usługi z niestandardowego `<cacheServiceAddress>` element podrzędny elementu `<sessionSecurityTokenCache>` elementu. Używa ona tego punktu końcowego, aby zainicjować `ISessionSecurityTokenCacheService` kanału, przez który może komunikować się z usługą.  W tym przykładzie, nie wszystkie metody trzeba do zaimplementowania <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy są wyświetlane w celu skrócenia programu.  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [Zarządzanie sesjami programu WIF](../../../docs/framework/security/wif-session-management.md)
