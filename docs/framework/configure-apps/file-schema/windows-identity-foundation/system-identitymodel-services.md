---
title: '&lt;system.identityModel.services&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: c7261d20ae2379ad33679cadecdef484f2afdecf
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778084"
---
# <a name="ltsystemidentitymodelservicesgt"></a><span data-ttu-id="c8987-102">&lt;system.identityModel.services&gt;</span><span class="sxs-lookup"><span data-stu-id="c8987-102">&lt;system.identityModel.services&gt;</span></span>
<span data-ttu-id="c8987-103">Sekcja konfiguracji uwierzytelniania przy użyciu protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="c8987-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="c8987-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="c8987-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8987-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8987-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8987-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8987-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c8987-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8987-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8987-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8987-108">Attributes</span></span>  
 <span data-ttu-id="c8987-109">Brak</span><span class="sxs-lookup"><span data-stu-id="c8987-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c8987-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8987-110">Child Elements</span></span>  
  
|<span data-ttu-id="c8987-111">Element</span><span class="sxs-lookup"><span data-stu-id="c8987-111">Element</span></span>|<span data-ttu-id="c8987-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c8987-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8987-113">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c8987-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="c8987-114">Zawiera ustawienia, które skonfigurować <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> moduły HTTP (SAM).</span><span class="sxs-lookup"><span data-stu-id="c8987-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8987-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8987-115">Parent Elements</span></span>  
 <span data-ttu-id="c8987-116">Brak</span><span class="sxs-lookup"><span data-stu-id="c8987-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8987-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8987-117">Remarks</span></span>  
 <span data-ttu-id="c8987-118">Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracji aplikacji, aby określić ustawienia SAM i WSFAM.</span><span class="sxs-lookup"><span data-stu-id="c8987-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8987-119">Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach, w kodzie, Menedżer autoryzacji oświadczeń (<xref:System.Security.Claims.ClaimsAuthorizationManager>) i zasad, który służy do podejmowania decyzji dotyczących autoryzacji są konfigurowane za pośrednictwem `<identityConfiguration>` element, który jest niejawnie lub jawnie odwoływać się z `<federationConfiguration>` elementu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="c8987-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="c8987-120">Aby uzyskać więcej informacji, zobacz **uwagi** w obszarze [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="c8987-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="c8987-121">`<system.identityModel.services>` Sekcji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> klasy.</span><span class="sxs-lookup"><span data-stu-id="c8987-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="c8987-122">Kolekcja podrzędnych `<federationConfiguration>` elementów skonfigurowanych w sekcji jest reprezentowany przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="c8987-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8987-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8987-123">Example</span></span>  
 <span data-ttu-id="c8987-124">Następujący kody XML pokazuje sposób dodawania `<system.identityModel.services>` sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8987-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="c8987-125">Należy najpierw dodać deklaracje sekcji dla obu `<system.identityModel.services>` sekcji i `<system.identityModel>` sekcje.</span><span class="sxs-lookup"><span data-stu-id="c8987-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="c8987-126">(Po dodaniu `<system.identityModel.services>` sekcji, należy również dodać deklarację dla `<system.identityModel>` sekcji, aby upewnić się, że domyślny `<identityConfiguration>` sekcji mogą być tworzone przez środowisko wykonawcze, jeśli to konieczne.) Po dodaniu deklaracje sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w ramach `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c8987-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
