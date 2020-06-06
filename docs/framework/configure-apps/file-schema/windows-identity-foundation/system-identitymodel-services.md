---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152507"
---
# \<system.identityModel.services>
<span data-ttu-id="813a5-102">Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="813a5-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="813a5-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="813a5-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="813a5-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="813a5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="813a5-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="813a5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="813a5-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="813a5-106">Attributes</span></span>  
 <span data-ttu-id="813a5-107">Brak</span><span class="sxs-lookup"><span data-stu-id="813a5-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="813a5-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="813a5-108">Child Elements</span></span>  
  
|<span data-ttu-id="813a5-109">Element</span><span class="sxs-lookup"><span data-stu-id="813a5-109">Element</span></span>|<span data-ttu-id="813a5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="813a5-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="813a5-111">Zawiera ustawienia służące do konfigurowania <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> modułów HTTP (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam).</span><span class="sxs-lookup"><span data-stu-id="813a5-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="813a5-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="813a5-112">Parent Elements</span></span>  
 <span data-ttu-id="813a5-113">Brak</span><span class="sxs-lookup"><span data-stu-id="813a5-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="813a5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="813a5-114">Remarks</span></span>  
 <span data-ttu-id="813a5-115">Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracji aplikacji, aby podać ustawienia dla sam i WSFAM.</span><span class="sxs-lookup"><span data-stu-id="813a5-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="813a5-116">Przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub klasy w <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, Menedżer autoryzacji oświadczeń ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) i zasady, które są używane do podejmowania decyzji dotyczących autoryzacji, są konfigurowane za pośrednictwem `<identityConfiguration>` elementu, który jest niejawnie lub jawnie przywoływany z `<federationConfiguration>` elementu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="813a5-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="813a5-117">Aby uzyskać więcej informacji, zobacz **uwagi** w obszarze [\<federationConfiguration>](federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="813a5-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="813a5-118">`<system.identityModel.services>`Sekcja jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> klasę.</span><span class="sxs-lookup"><span data-stu-id="813a5-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="813a5-119">Kolekcja `<federationConfiguration>` elementów podrzędnych skonfigurowanych w sekcji jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> klasę.</span><span class="sxs-lookup"><span data-stu-id="813a5-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="813a5-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="813a5-120">Example</span></span>  
 <span data-ttu-id="813a5-121">Poniższy kod XML pokazuje, jak dodać `<system.identityModel.services>` sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="813a5-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="813a5-122">Należy najpierw dodać deklaracje sekcji dla `<system.identityModel.services>` sekcji i części `<system.identityModel>` .</span><span class="sxs-lookup"><span data-stu-id="813a5-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="813a5-123">(Po dodaniu `<system.identityModel.services>` sekcji należy również dodać deklarację dla `<system.identityModel>` sekcji, aby upewnić się, że w `<identityConfiguration>` razie potrzeby środowisko uruchomieniowe może utworzyć domyślną sekcję). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="813a5-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
