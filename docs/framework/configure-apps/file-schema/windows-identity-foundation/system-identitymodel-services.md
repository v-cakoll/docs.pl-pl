---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152507"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="e7f08-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="e7f08-102">\<system.identityModel.services></span></span>
<span data-ttu-id="e7f08-103">Sekcja Konfiguracji uwierzytelniania przy użyciu protokołu Federacji WS.</span><span class="sxs-lookup"><span data-stu-id="e7f08-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="e7f08-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e7f08-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e7f08-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span><span class="sxs-lookup"><span data-stu-id="e7f08-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f08-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7f08-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7f08-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7f08-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e7f08-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7f08-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7f08-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7f08-109">Attributes</span></span>  
 <span data-ttu-id="e7f08-110">Brak</span><span class="sxs-lookup"><span data-stu-id="e7f08-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7f08-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7f08-111">Child Elements</span></span>  
  
|<span data-ttu-id="e7f08-112">Element</span><span class="sxs-lookup"><span data-stu-id="e7f08-112">Element</span></span>|<span data-ttu-id="e7f08-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e7f08-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7f08-114">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="e7f08-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="e7f08-115">Zawiera ustawienia, które <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> konfigurują moduły HTTP <xref:System.IdentityModel.Services.SessionAuthenticationModule> (WSFAM) i (SAM).</span><span class="sxs-lookup"><span data-stu-id="e7f08-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7f08-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7f08-116">Parent Elements</span></span>  
 <span data-ttu-id="e7f08-117">Brak</span><span class="sxs-lookup"><span data-stu-id="e7f08-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7f08-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7f08-118">Remarks</span></span>  
 <span data-ttu-id="e7f08-119">Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracyjnego aplikacji, aby zapewnić ustawienia dla SAM i WSFAM.</span><span class="sxs-lookup"><span data-stu-id="e7f08-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e7f08-120">Podczas korzystania <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> z <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy do zapewnienia kontroli dostępu na podstawie<xref:System.Security.Claims.ClaimsAuthorizationManager>oświadczeń w kodzie, menedżer autoryzacji oświadczeń ( `<identityConfiguration>` ) i zasady, które jest `<federationConfiguration>` używany do podejmowania decyzji autoryzacji są konfigurowane za pośrednictwem elementu, który jest niejawnie lub jawnie odwołuje się z elementu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e7f08-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="e7f08-121">Aby uzyskać więcej informacji, zobacz **Uwagi** w [ \<obszarze federationConfiguration>](federationconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="e7f08-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="e7f08-122">Sekcja `<system.identityModel.services>` jest reprezentowana <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="e7f08-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="e7f08-123">Kolekcja elementów `<federationConfiguration>` podrzędnych skonfigurowanych w sekcji <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> jest reprezentowana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="e7f08-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7f08-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7f08-124">Example</span></span>  
 <span data-ttu-id="e7f08-125">Poniższy kod XML pokazuje, jak dodać sekcję `<system.identityModel.services>` do pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="e7f08-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="e7f08-126">Należy najpierw dodać deklaracje sekcji `<system.identityModel.services>` zarówno `<system.identityModel>` dla sekcji, jak i sekcji.</span><span class="sxs-lookup"><span data-stu-id="e7f08-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="e7f08-127">(Podczas dodawania `<system.identityModel.services>` sekcji należy również dodać deklarację dla `<system.identityModel>` sekcji, `<identityConfiguration>` aby upewnić się, że domyślna sekcja może zostać utworzona przez środowisko wykonawcze, jeśli to konieczne). Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w `<system.identityModel.services>` ramach elementu.</span><span class="sxs-lookup"><span data-stu-id="e7f08-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
