---
title: WIF i farmy serwerów sieci Web
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ed6a7fbe550dad85cf505eaf20a446803b84c96f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410419"
---
# <a name="wif-and-web-farms"></a>WIF i farmy serwerów sieci Web
Korzystając z programu Windows Identity Foundation (WIF) do zabezpieczania zasobów jednostki uzależnionej aplikacji firmy (RP), które zostało wdrożone w farmie sieci web, należy wykonać określone kroki, aby upewnić się, że WIF może przetwarzać tokenów z wystąpień RP aplikacji uruchomionych na różnych komputery z farmy. Proces przetwarzania obejmuje sprawdzanie poprawności Podpisy tokenu sesji, szyfrowania i odszyfrowywania tokenów sesji, buforowanie tokeny sesji i wykrywanie odtwarzany tokenów zabezpieczających.  
  
 W przypadku typowej gdy WIF służy do zabezpieczania zasobów aplikacji RP — czy RP działa na pojedynczym komputerze lub w kolektywie serwerów sieci web--sesji jest nawiązywane z klienta na podstawie tokenów zabezpieczeń, który został uzyskany z usługi tokenu zabezpieczającego (STS). Pozwoli to uniknąć wymuszania klienta do uwierzytelniania na STS dla każdego zasobu jest zabezpieczone przy użyciu WIF aplikacji. Aby uzyskać więcej informacji na temat obsługi WIF sesji, zobacz [WIF sesji zarządzania](../../../docs/framework/security/wif-session-management.md).  
  
 Gdy używane są ustawienia domyślne, WIF wykonuje następujące czynności:  
  
-   Używa wystąpienia <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy do odczytu i zapisu tokenu sesji (wystąpienie <xref:System.IdentityModel.Tokens.SessionSecurityToken> klasy) która prowadzi oświadczenia i innych informacji o tokenie zabezpieczającym, który był używany do uwierzytelniania, a także informacje o sesji samego siebie. Tokenu sesji zostaje spakowany i przechowywane w pliku cookie sesji. Domyślnie <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> używa <xref:System.IdentityModel.ProtectedDataCookieTransform> klasy, która używa interfejsu API ochrony danych (DPAPI), aby chronić tokenu sesji. DPAPI zapewnia ochronę przy użyciu poświadczeń użytkownika lub komputera i przechowuje dane klucza w profilu użytkownika.  
  
-   Używa domyślnej, wykonania w pamięci <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy do przechowywania i przetwarzania tokenu sesji.  
  
 Te ustawienia domyślne działają w scenariuszach, w których aplikacja RP jest wdrażana na pojedynczym komputerze; Jednak po wdrożeniu na farmie sieci web każde żądanie HTTP mogą być wysyłane do i przetwarzane przez inne wystąpienie aplikacji planu odzyskiwania uruchomiony na innym komputerze. Domyślne ustawienia WIF opisane powyżej w tym scenariuszu nie będą działać, ponieważ token ochrony i buforowania tokenu są zależne od określonego komputera.  
  
 Aby wdrożyć aplikację planu odzyskiwania w farmie sieci web, należy upewnić przetwarzania tokenów sesji (a także powtórzony tokenów) nie jest zależna od aplikacja była uruchomiona na określonym komputerze. Aby zrobić to do wdrożenia aplikacji planu odzyskiwania, tak aby były używane funkcje udostępniane przez platformę ASP.NET `<machineKey>` element konfiguracji zawiera systemy buforowania rozproszonego przetwarzania tokenów sesji i odtwarzany tokenów. `<machineKey>` Element umożliwia określenie klucze wymagane do weryfikacji, szyfrowania i odszyfrowywania tokenów w pliku konfiguracji, który umożliwia określenie tych samych kluczy na różnych komputerach w farmie sieci web. WIF zawiera specjalne sesji programu obsługi tokenów, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, która chroni tokeny przy użyciu kluczy określona w `<machineKey>` elementu. Do wdrożenia tej strategii, należy wykonać następujące wytyczne:  
  
-   Za pomocą programu ASP.NET `<machineKey>` element w konfiguracji, aby jawnie określić klucze podpisywania i szyfrowania, które mogą być używane na komputerach w farmie. Następujący kod XML zawiera specyfikację `<machineKey>` elementu w obszarze `<system.web>` w pliku konfiguracji.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Konfigurowanie aplikacji do korzystania z <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> przez dodanie go do kolekcji programu obsługi tokenów. Należy najpierw usunąć <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (lub pochodny żadnych obsługi <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy) z kolekcji programu obsługi tokenów, jeśli program obsługi jest obecny. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> Używa <xref:System.IdentityModel.Services.MachineKeyTransform> klasy, która chroni dane pliku cookie sesji przy użyciu kryptograficznych materiałów, określonych w `<machineKey>` elementu. Następujący kod XML przedstawiono sposób dodawania <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> do kolekcji programu obsługi tokenów.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Pochodzić od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> i wdrożenie rozproszone buforowania, czyli pamięci podręcznej, który jest dostępny ze wszystkich komputerów w farmie serwerów, na którym planu odzyskiwania mogą zostać uruchomione. Konfigurowanie planu odzyskiwania, aby użyć rozproszonej pamięci podręcznej, określając [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) w pliku konfiguracji. Można zastąpić <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metody w klasie pochodnej, aby zaimplementować elementy podrzędne `<sessionSecurityTokenCache>` elementu, jeśli są wymagane.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Jednym ze sposobów zaimplementować systemy buforowania rozproszonego jest zapewnienie WCF frontonu dla niestandardowych pamięci podręcznej. Aby uzyskać więcej informacji o implementacji WCF, buforowanie usługi, zobacz [usługi WCF buforowanie](#BKMK_TheWCFCachingService). Aby uzyskać więcej informacji o implementacji klienta WCF, służącego do wywoływania usługi buforowania aplikacji planu odzyskiwania, zobacz [WCF buforowanie klient](#BKMK_TheWCFClient).  
  
-   W przypadku wykrycia przez aplikację tokenów powtórzony należy wykonać podobne rozproszonej pamięci podręcznej strategii dla pamięci podręcznej powtórzeń tokenów przez wynikających z <xref:System.IdentityModel.Tokens.TokenReplayCache> i wskazujący Twojej powtórzeń tokenów buforowanie usługi w [ \< tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element konfiguracji.  
  
> [!IMPORTANT]
>  Wszystkie przykładowe XML i kodu w tym temacie jest pobierana z [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) próbki.  
  
> [!IMPORTANT]
>  Przykłady w tym temacie podano jako — jest i nie są przeznaczone do użycia w kodzie produkcyjnym bez żadnych modyfikacji.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Buforowanie usługi WCF  
 Następujący interfejs definiuje kontrakt między usługą buforowania WCF i klienta WCF, używany przez aplikację jednostki uzależnionej strony do komunikowania się z nim. Zasadniczo udostępnia metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy jako operacji usługi.  
  
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
  
 Poniższy kod przedstawia implementację usługi WCF buforowanie usługi. W tym przykładzie wartość domyślna implementowane przez WIF pamięci podręcznej tokenu sesji w pamięci jest używany. Alternatywnie można zaimplementować trwałej pamięci podręcznej przechowywana w bazie danych. `ISessionSecurityTokenCacheService` definiuje interfejs przedstawionych powyżej. W tym przykładzie nie wszystkie metody, musi implementować interfejs są wyświetlane dla skrócenia.  
  
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
## <a name="the-wcf-caching-client"></a>Buforowanie klienta WCF  
 W tej sekcji przedstawiono implementacji klasy, która jest pochodną <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> oraz że delegatów wywołania do usługi buforowania. Konfigurowanie aplikacji RP do korzystania z tej klasy przy użyciu [ \<sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element jak następujący kod XML  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 Przesłonięć klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodę, aby uzyskać punkt końcowy usługi z niestandardowego `<cacheServiceAddress>` elementem podrzędnym `<sessionSecurityTokenCache>` elementu. Używa tego punktu końcowego, aby zainicjować `ISessionSecurityTokenCacheService` kanału, przez który może komunikować się z usługą.  W tym przykładzie nie wszystkie metody wymagane do zaimplementowania <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy są wyświetlane dla skrócenia.  
  
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
