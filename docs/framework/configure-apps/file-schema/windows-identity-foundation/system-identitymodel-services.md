---
title: '&lt;system.identityModel.services&gt;'
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca108d7dd0498b0d7c08bb632ab45c7229ff58c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757050"
---
# <a name="ltsystemidentitymodelservicesgt"></a><span data-ttu-id="1b013-102">&lt;system.identityModel.services&gt;</span><span class="sxs-lookup"><span data-stu-id="1b013-102">&lt;system.identityModel.services&gt;</span></span>
<span data-ttu-id="1b013-103">Sekcja konfiguracyjna do uwierzytelniania przy użyciu protokołu WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="1b013-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="1b013-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="1b013-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b013-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b013-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b013-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1b013-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1b013-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1b013-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b013-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b013-108">Attributes</span></span>  
 <span data-ttu-id="1b013-109">Brak</span><span class="sxs-lookup"><span data-stu-id="1b013-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b013-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b013-110">Child Elements</span></span>  
  
|<span data-ttu-id="1b013-111">Element</span><span class="sxs-lookup"><span data-stu-id="1b013-111">Element</span></span>|<span data-ttu-id="1b013-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1b013-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b013-113">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1b013-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="1b013-114">Zawiera ustawienia, które konfigurują <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) i <xref:System.IdentityModel.Services.SessionAuthenticationModule> moduły HTTP (SAM).</span><span class="sxs-lookup"><span data-stu-id="1b013-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b013-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b013-115">Parent Elements</span></span>  
 <span data-ttu-id="1b013-116">Brak</span><span class="sxs-lookup"><span data-stu-id="1b013-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b013-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b013-117">Remarks</span></span>  
 <span data-ttu-id="1b013-118">Dodaj `<system.identityModel.services>` sekcję do pliku konfiguracji aplikacji, aby określić ustawienia SAM i WSFAM.</span><span class="sxs-lookup"><span data-stu-id="1b013-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1b013-119">Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie programu Menedżer autoryzacji oświadczeń (<xref:System.Security.Claims.ClaimsAuthorizationManager>) i zasad, która umożliwia podjęcie decyzji dotyczących autoryzacji są skonfigurowane za pomocą `<identityConfiguration>` element, który jest jawnie lub niejawnie wywoływany przez `<federationConfiguration>` element w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1b013-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="1b013-120">Aby uzyskać więcej informacji, zobacz **uwagi** w obszarze [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1b013-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="1b013-121">`<system.identityModel.services>` Sekcji jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1b013-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="1b013-122">Kolekcja podrzędnych `<federationConfiguration>` skonfigurowane w sekcji elementów jest reprezentowana przez <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1b013-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b013-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b013-123">Example</span></span>  
 <span data-ttu-id="1b013-124">Następujący kod XML przedstawiono sposób dodawania `<system.identityModel.services>` sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1b013-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="1b013-125">Najpierw należy dodać deklaracje sekcji zarówno `<system.identityModel.services>` sekcji i `<system.identityModel>` sekcje.</span><span class="sxs-lookup"><span data-stu-id="1b013-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="1b013-126">(Po dodaniu `<system.identityModel.services>` sekcji, należy również dodać deklaracji `<system.identityModel>` sekcji, aby upewnić się, że domyślna `<identityConfiguration>` sekcji można tworzyć w czasie wykonywania, jeśli jest to konieczne.) Po dodaniu deklaracji sekcji można skonfigurować ustawienia uwierzytelniania federacyjnego w obszarze `<system.identityModel.services>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1b013-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
