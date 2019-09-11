---
title: Program WIF i farmy serwerów internetowych
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 09d5f3f745f170439a7fbf160b78439c103623b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851525"
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="de938-102">Program WIF i farmy serwerów internetowych</span><span class="sxs-lookup"><span data-stu-id="de938-102">WIF and Web Farms</span></span>
<span data-ttu-id="de938-103">W przypadku korzystania z programu Windows Identity Foundation (WIF) w celu zabezpieczenia zasobów jednostki uzależnionej (RP) wdrożonej w kolektywie serwerów sieci Web należy wykonać określone kroki, aby upewnić się, że WIF może przetwarzać tokeny z wystąpień aplikacji RP uruchomionej w różnych Komputery w farmie.</span><span class="sxs-lookup"><span data-stu-id="de938-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="de938-104">Przetwarzanie obejmuje sprawdzanie poprawności sygnatur tokenów sesji, szyfrowanie i odszyfrowywanie tokenów sesji, buforowanie tokenów sesji oraz Wykrywanie powtarzających się tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="de938-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="de938-105">W typowym przypadku, gdy WIF jest używany do zabezpieczania zasobów aplikacji RP — czy jednostka UZALEŻNIONa jest uruchomiona na pojedynczym komputerze lub w kolektywie serwerów sieci Web — sesja jest ustanawiana z klientem na podstawie tokenu zabezpieczającego uzyskanego z usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="de938-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="de938-106">Ma to na celu uniknięcie wymuszenia uwierzytelniania klienta w usłudze STS dla każdego zasobu aplikacji, który jest zabezpieczony za pomocą WIF.</span><span class="sxs-lookup"><span data-stu-id="de938-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="de938-107">Aby uzyskać więcej informacji o tym, jak WIF obsługuje sesje, zobacz [Zarządzanie sesją WIF](../../../docs/framework/security/wif-session-management.md).</span><span class="sxs-lookup"><span data-stu-id="de938-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="de938-108">Gdy są używane ustawienia domyślne, WIF wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="de938-108">When default settings are used, WIF does the following:</span></span>  
  
- <span data-ttu-id="de938-109">Używa wystąpienia <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy do odczytu i zapisu tokenu sesji (wystąpienie <xref:System.IdentityModel.Tokens.SessionSecurityToken> klasy), które przenosi oświadczenia i inne informacje o tokenie zabezpieczającym, który został użyty do uwierzytelniania, a także informacje o sesji sam.</span><span class="sxs-lookup"><span data-stu-id="de938-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="de938-110">Token sesji jest spakowany i przechowywany w pliku cookie sesji.</span><span class="sxs-lookup"><span data-stu-id="de938-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="de938-111">Domyślnie program <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> <xref:System.IdentityModel.ProtectedDataCookieTransform> używa klasy, która używa interfejsu API ochrony danych (DPAPI) do ochrony tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="de938-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="de938-112">DPAPI zapewnia ochronę przy użyciu poświadczeń użytkownika lub komputera i przechowuje dane klucza w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de938-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
- <span data-ttu-id="de938-113">Używa domyślnej implementacji <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy w pamięci do przechowywania i przetwarzania tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="de938-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="de938-114">Te ustawienia domyślne działają w scenariuszach, w których aplikacja RP jest wdrażana na pojedynczym komputerze; Jednak po wdrożeniu w kolektywie serwerów sieci Web każde żądanie HTTP może zostać wysłane do i przetworzone przez inne wystąpienie aplikacji RP uruchomionej na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="de938-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="de938-115">W tym scenariuszu domyślne ustawienia WIF opisane powyżej nie będą działały, ponieważ zarówno ochrona tokenów, jak i buforowanie tokenów są zależne od określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="de938-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="de938-116">Aby wdrożyć aplikację RP w kolektywie serwerów sieci Web, należy się upewnić, że przetwarzanie tokenów sesji (jak również w przypadku ponownie uruchomionych tokenów) nie jest zależne od aplikacji uruchomionej na określonym komputerze.</span><span class="sxs-lookup"><span data-stu-id="de938-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="de938-117">Jednym ze sposobów wykonania tej czynności jest zaimplementowanie aplikacji RP w taki sposób, aby korzystała z funkcji `<machineKey>` udostępnianych przez element konfiguracji ASP.NET i udostępnia rozproszone buforowanie na potrzeby przetwarzania tokenów sesji i ponownie odtwarzanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="de938-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="de938-118">`<machineKey>` Element pozwala określić klucze potrzebne do walidacji, szyfrowania i odszyfrowywania tokenów w pliku konfiguracji, co umożliwia określenie tych samych kluczy na różnych komputerach w kolektywie serwerów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="de938-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="de938-119">WIF udostępnia wyspecjalizowaną procedurę obsługi tokenów sesji <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, która chroni tokeny przy użyciu kluczy określonych `<machineKey>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="de938-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="de938-120">Aby zaimplementować tę strategię, można przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="de938-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
- <span data-ttu-id="de938-121">Użyj elementu ASP.NET `<machineKey>` w konfiguracji, aby jawnie określić klucze podpisywania i szyfrowania, które mogą być używane na różnych komputerach w farmie.</span><span class="sxs-lookup"><span data-stu-id="de938-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="de938-122">Poniższy kod XML przedstawia specyfikację `<machineKey>` elementu `<system.web>` w elemencie w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="de938-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- <span data-ttu-id="de938-123">Skonfiguruj aplikację do użycia <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> przez dodanie jej do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="de938-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="de938-124">Należy najpierw usunąć <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (lub wszelkie procedury obsługi pochodzące <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> z klasy) z kolekcji programu obsługi tokenów, jeśli taka procedura obsługi jest obecna.</span><span class="sxs-lookup"><span data-stu-id="de938-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="de938-125">Używa klasy, która chroni dane plików cookie sesji za pomocą materiału `<machineKey>` kryptograficznego określonego w elemencie. <xref:System.IdentityModel.Services.MachineKeyTransform> <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="de938-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="de938-126">Poniższy kod XML przedstawia sposób dodawania <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="de938-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- <span data-ttu-id="de938-127">Pochodzą z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> i Implementuj rozproszone buforowanie, czyli pamięć podręczną, która jest dostępna ze wszystkich komputerów w farmie, w której może zostać uruchomiony system RP.</span><span class="sxs-lookup"><span data-stu-id="de938-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="de938-128">Skonfiguruj składnik RP, aby używał rozproszonej pamięci podręcznej przez określenie [ \<elementu sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="de938-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="de938-129">Można zastąpić <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> metodę w klasie pochodnej, aby zaimplementować elementy podrzędne elementu, `<sessionSecurityTokenCache>` jeśli są wymagane.</span><span class="sxs-lookup"><span data-stu-id="de938-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="de938-130">Jednym ze sposobów implementacji rozproszonej pamięci podręcznej jest zapewnienie frontonu programu WCF dla niestandardową pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="de938-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="de938-131">Aby uzyskać więcej informacji na temat implementowania usługi buforowania WCF, zobacz [Usługa buforowania WCF](#BKMK_TheWCFCachingService).</span><span class="sxs-lookup"><span data-stu-id="de938-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="de938-132">Aby uzyskać więcej informacji na temat implementowania klienta WCF, który może być używany przez aplikację RP do wywoływania usługi buforowania, zobacz [klienta buforowania WCF](#BKMK_TheWCFClient).</span><span class="sxs-lookup"><span data-stu-id="de938-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
- <span data-ttu-id="de938-133">Jeśli aplikacja wykryje ponownie uruchomione tokeny, należy przestrzegać podobnej strategii rozproszonej pamięci podręcznej dla buforu powtarzania tokenów, pobierając z <xref:System.IdentityModel.Tokens.TokenReplayCache> i wskazując usługę buforowania powtarzania tokenów [ \<w tokenReplayCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="de938-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="de938-134">Wszystkie przykładowe XML i kod w tym temacie są pobierane z przykładu [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) .</span><span class="sxs-lookup"><span data-stu-id="de938-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="de938-135">Przykłady w tym temacie są podane jako-is i nie są przeznaczone do użycia w kodzie produkcyjnym bez modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="de938-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="de938-136">Usługa buforowania WCF</span><span class="sxs-lookup"><span data-stu-id="de938-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="de938-137">Poniższy interfejs definiuje umowę między usługą buforowania WCF i klientem WCF używanym przez aplikację jednostki uzależnionej do komunikowania się z nią.</span><span class="sxs-lookup"><span data-stu-id="de938-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="de938-138">Zasadniczo uwidacznia metody <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy jako operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="de938-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="de938-139">Poniższy kod przedstawia implementację usługi buforowania WCF.</span><span class="sxs-lookup"><span data-stu-id="de938-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="de938-140">W tym przykładzie użyto domyślnej pamięci podręcznej tokenu sesji w pamięci wdrożonej przez WIF.</span><span class="sxs-lookup"><span data-stu-id="de938-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="de938-141">Alternatywnie, można zaimplementować trwałą pamięć podręczną w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="de938-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="de938-142">`ISessionSecurityTokenCacheService`definiuje opisany powyżej interfejs.</span><span class="sxs-lookup"><span data-stu-id="de938-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="de938-143">W tym przykładzie nie wszystkie metody wymagane do zaimplementowania interfejsu są wyświetlane dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="de938-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```csharp
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
## <a name="the-wcf-caching-client"></a><span data-ttu-id="de938-144">Klient buforowania WCF</span><span class="sxs-lookup"><span data-stu-id="de938-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="de938-145">W tej sekcji przedstawiono implementację klasy, która pochodzi od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> i która deleguje wywołania do usługi buforowania.</span><span class="sxs-lookup"><span data-stu-id="de938-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="de938-146">Aplikację RP można skonfigurować tak, aby używała tej klasy za pomocą [ \<elementu sessionSecurityTokenCache >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) , jak w poniższym kodzie XML</span><span class="sxs-lookup"><span data-stu-id="de938-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="de938-147">Klasa przesłania <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> metodę, aby uzyskać punkt końcowy usługi z niestandardowego `<cacheServiceAddress>` elementu `<sessionSecurityTokenCache>` podrzędnego elementu.</span><span class="sxs-lookup"><span data-stu-id="de938-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="de938-148">Używa tego punktu końcowego do zainicjowania `ISessionSecurityTokenCacheService` kanału, w którym może komunikować się z usługą.</span><span class="sxs-lookup"><span data-stu-id="de938-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="de938-149">W tym przykładzie nie wszystkie metody wymagane do zaimplementowania <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy są wyświetlane dla zwięzłości.</span><span class="sxs-lookup"><span data-stu-id="de938-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="de938-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de938-150">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [<span data-ttu-id="de938-151">Zarządzanie sesjami programu WIF</span><span class="sxs-lookup"><span data-stu-id="de938-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
