---
title: '&lt;system.identityModel&gt;'
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 1b3121a6e7e036ec268cf83ffbf545c0e669a9b9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199399"
---
# <a name="ltsystemidentitymodelgt"></a><span data-ttu-id="3daf8-102">&lt;system.identityModel&gt;</span><span class="sxs-lookup"><span data-stu-id="3daf8-102">&lt;system.identityModel&gt;</span></span>
<span data-ttu-id="3daf8-103">Udostępnia konfigurację dla Włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="3daf8-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="3daf8-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3daf8-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3daf8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3daf8-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3daf8-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3daf8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3daf8-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3daf8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3daf8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3daf8-108">Attributes</span></span>  
 <span data-ttu-id="3daf8-109">Brak</span><span class="sxs-lookup"><span data-stu-id="3daf8-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3daf8-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3daf8-110">Child Elements</span></span>  
  
|<span data-ttu-id="3daf8-111">Element</span><span class="sxs-lookup"><span data-stu-id="3daf8-111">Element</span></span>|<span data-ttu-id="3daf8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3daf8-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3daf8-113">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3daf8-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="3daf8-114">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="3daf8-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3daf8-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3daf8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3daf8-116">Element</span><span class="sxs-lookup"><span data-stu-id="3daf8-116">Element</span></span>|<span data-ttu-id="3daf8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3daf8-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="3daf8-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3daf8-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3daf8-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3daf8-119">Remarks</span></span>  
 <span data-ttu-id="3daf8-120">Dodaj `<system.identityModel>` sekcję do pliku konfiguracji, aby skonfigurować usługi lub aplikacji do korzystania z usługi Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="3daf8-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="3daf8-121">`<system.identityModel>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> klasy.</span><span class="sxs-lookup"><span data-stu-id="3daf8-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3daf8-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3daf8-122">Example</span></span>  
 <span data-ttu-id="3daf8-123">Poniższy przykład pokazuje, jak dodać `<system.identityModel>` sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3daf8-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="3daf8-124">Należy najpierw dodać konfiguracji sekcji i przestrzeń nazw deklaracji w obszarze `<configSections>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3daf8-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="3daf8-125">Następnie można dodać `<system.IdentityModel>` elementu do pliku konfiguracji w celu określenia co najmniej jedna konfiguracja tożsamości.</span><span class="sxs-lookup"><span data-stu-id="3daf8-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3daf8-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3daf8-126">See Also</span></span>  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
