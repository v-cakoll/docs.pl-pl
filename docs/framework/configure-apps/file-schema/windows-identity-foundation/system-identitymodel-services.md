---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943656"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="70ccd-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="70ccd-102">\<system.identityModel.services></span></span>
<span data-ttu-id="70ccd-103">Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="70ccd-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="70ccd-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="70ccd-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70ccd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="70ccd-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70ccd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70ccd-106">Attributes and Elements</span></span>  
 <span data-ttu-id="70ccd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70ccd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70ccd-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70ccd-108">Attributes</span></span>  
 <span data-ttu-id="70ccd-109">Brak</span><span class="sxs-lookup"><span data-stu-id="70ccd-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70ccd-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70ccd-110">Child Elements</span></span>  
  
|<span data-ttu-id="70ccd-111">Element</span><span class="sxs-lookup"><span data-stu-id="70ccd-111">Element</span></span>|<span data-ttu-id="70ccd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="70ccd-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70ccd-113">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="70ccd-113">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="70ccd-114">Zawiera ustawienia służące do <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurowania modułów HTTP (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).</span><span class="sxs-lookup"><span data-stu-id="70ccd-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70ccd-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70ccd-115">Parent Elements</span></span>  
 <span data-ttu-id="70ccd-116">Brak</span><span class="sxs-lookup"><span data-stu-id="70ccd-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70ccd-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70ccd-117">Remarks</span></span>  
 <span data-ttu-id="70ccd-118">`<system.identityModel.services>` Dodaj sekcję do pliku konfiguracji aplikacji, aby podać ustawienia dla sam i WSFAM.</span><span class="sxs-lookup"><span data-stu-id="70ccd-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="70ccd-119">Przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.Security.Claims.ClaimsAuthorizationManager>lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, Menedżer autoryzacji oświadczeń () i zasady służące `<identityConfiguration>` do podejmowania decyzji dotyczących autoryzacji są konfigurowane za pośrednictwem <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> element, który jest niejawnie lub jawnie przywoływany z `<federationConfiguration>` elementu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="70ccd-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="70ccd-120">Aby uzyskać więcej informacji, zobacz **uwagi** poniżej [ \<elementu federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="70ccd-120">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="70ccd-121">Sekcja jest reprezentowana <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> przez klasę. `<system.identityModel.services>`</span><span class="sxs-lookup"><span data-stu-id="70ccd-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="70ccd-122">Kolekcja elementów podrzędnych `<federationConfiguration>` skonfigurowanych w sekcji jest reprezentowana <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="70ccd-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70ccd-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="70ccd-123">Example</span></span>  
 <span data-ttu-id="70ccd-124">Poniższy kod XML pokazuje, `<system.identityModel.services>` jak dodać sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="70ccd-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="70ccd-125">Należy najpierw dodać deklaracje sekcji dla `<system.identityModel.services>` sekcji `<system.identityModel>` i części.</span><span class="sxs-lookup"><span data-stu-id="70ccd-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="70ccd-126">(Po dodaniu `<system.identityModel.services>` sekcji należy również dodać deklarację `<system.identityModel>` dla sekcji, aby upewnić się, że w razie `<identityConfiguration>` potrzeby środowisko uruchomieniowe może utworzyć domyślną sekcję). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="70ccd-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
