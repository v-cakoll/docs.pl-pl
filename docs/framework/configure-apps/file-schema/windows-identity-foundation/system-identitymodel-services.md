---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e9488c0681e1a5f0fe94112a36b65ec73bf9fd09
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251808"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="822e9-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="822e9-102">\<system.identityModel.services></span></span>
<span data-ttu-id="822e9-103">Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="822e9-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="822e9-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="822e9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="822e9-105">&nbsp;&nbsp; **\<> System. identityModel. Services**</span><span class="sxs-lookup"><span data-stu-id="822e9-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="822e9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="822e9-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="822e9-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="822e9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="822e9-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="822e9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="822e9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="822e9-109">Attributes</span></span>  
 <span data-ttu-id="822e9-110">Brak</span><span class="sxs-lookup"><span data-stu-id="822e9-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="822e9-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="822e9-111">Child Elements</span></span>  
  
|<span data-ttu-id="822e9-112">Element</span><span class="sxs-lookup"><span data-stu-id="822e9-112">Element</span></span>|<span data-ttu-id="822e9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="822e9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="822e9-114">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="822e9-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="822e9-115">Zawiera ustawienia służące do <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurowania modułów HTTP (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> i (sam).</span><span class="sxs-lookup"><span data-stu-id="822e9-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="822e9-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="822e9-116">Parent Elements</span></span>  
 <span data-ttu-id="822e9-117">Brak</span><span class="sxs-lookup"><span data-stu-id="822e9-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="822e9-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="822e9-118">Remarks</span></span>  
 <span data-ttu-id="822e9-119">`<system.identityModel.services>` Dodaj sekcję do pliku konfiguracji aplikacji, aby podać ustawienia dla sam i WSFAM.</span><span class="sxs-lookup"><span data-stu-id="822e9-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="822e9-120">Przy użyciu <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.Security.Claims.ClaimsAuthorizationManager>lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, Menedżer autoryzacji oświadczeń () i zasady służące `<identityConfiguration>` do podejmowania decyzji dotyczących autoryzacji są konfigurowane za pośrednictwem <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> element, który jest niejawnie lub jawnie przywoływany z `<federationConfiguration>` elementu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="822e9-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="822e9-121">Aby uzyskać więcej informacji, zobacz **uwagi** poniżej [ \<elementu federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="822e9-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="822e9-122">Sekcja jest reprezentowana <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> przez klasę. `<system.identityModel.services>`</span><span class="sxs-lookup"><span data-stu-id="822e9-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="822e9-123">Kolekcja elementów podrzędnych `<federationConfiguration>` skonfigurowanych w sekcji jest reprezentowana <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="822e9-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="822e9-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="822e9-124">Example</span></span>  
 <span data-ttu-id="822e9-125">Poniższy kod XML pokazuje, `<system.identityModel.services>` jak dodać sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="822e9-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="822e9-126">Należy najpierw dodać deklaracje sekcji dla `<system.identityModel.services>` sekcji `<system.identityModel>` i części.</span><span class="sxs-lookup"><span data-stu-id="822e9-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="822e9-127">(Po dodaniu `<system.identityModel.services>` sekcji należy również dodać deklarację `<system.identityModel>` dla sekcji, aby upewnić się, że w razie `<identityConfiguration>` potrzeby środowisko uruchomieniowe może utworzyć domyślną sekcję). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="822e9-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
