---
title: '&lt;system.identityModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 356dd1531f093282a1a8463b7d697400f8b45862
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemidentitymodelgt"></a><span data-ttu-id="dc2e7-102">&lt;system.identityModel&gt;</span><span class="sxs-lookup"><span data-stu-id="dc2e7-102">&lt;system.identityModel&gt;</span></span>
<span data-ttu-id="dc2e7-103">Zapewnia konfigurację Włączanie opcji Windows Identity Foundation (WIF) w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="dc2e7-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="dc2e7-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc2e7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc2e7-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc2e7-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dc2e7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dc2e7-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc2e7-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dc2e7-108">Attributes</span></span>  
 <span data-ttu-id="dc2e7-109">Brak</span><span class="sxs-lookup"><span data-stu-id="dc2e7-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dc2e7-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dc2e7-110">Child Elements</span></span>  
  
|<span data-ttu-id="dc2e7-111">Element</span><span class="sxs-lookup"><span data-stu-id="dc2e7-111">Element</span></span>|<span data-ttu-id="dc2e7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dc2e7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc2e7-113">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="dc2e7-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="dc2e7-114">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc2e7-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dc2e7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dc2e7-116">Element</span><span class="sxs-lookup"><span data-stu-id="dc2e7-116">Element</span></span>|<span data-ttu-id="dc2e7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="dc2e7-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="dc2e7-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc2e7-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc2e7-119">Remarks</span></span>  
 <span data-ttu-id="dc2e7-120">Dodaj `<system.identityModel>` sekcji pliku konfiguracji, aby skonfigurować usługę lub aplikację do używania systemu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="dc2e7-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="dc2e7-121">`<system.identityModel>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> klasy.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc2e7-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc2e7-122">Example</span></span>  
 <span data-ttu-id="dc2e7-123">Poniższy przykład przedstawia sposób dodawania `<system.identityModel>` sekcji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="dc2e7-124">Najpierw należy dodać konfiguracji deklaracji sekcji i przestrzeni nazw w obszarze `<configSections>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="dc2e7-125">Następnie można dodać `<system.IdentityModel>` elementu do pliku konfiguracji, aby określić co najmniej jednej konfiguracji tożsamości.</span><span class="sxs-lookup"><span data-stu-id="dc2e7-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc2e7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc2e7-126">See Also</span></span>  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
