---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 286ae88946692e6894ca3c7ee9e1348415c84ade
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943603"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="396ad-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="396ad-102">\<system.identityModel></span></span>
<span data-ttu-id="396ad-103">Zapewnia konfigurację umożliwiającą włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="396ad-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="396ad-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="396ad-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="396ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="396ad-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="396ad-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="396ad-106">Attributes and Elements</span></span>  
 <span data-ttu-id="396ad-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="396ad-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="396ad-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="396ad-108">Attributes</span></span>  
 <span data-ttu-id="396ad-109">Brak</span><span class="sxs-lookup"><span data-stu-id="396ad-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="396ad-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="396ad-110">Child Elements</span></span>  
  
|<span data-ttu-id="396ad-111">Element</span><span class="sxs-lookup"><span data-stu-id="396ad-111">Element</span></span>|<span data-ttu-id="396ad-112">Opis</span><span class="sxs-lookup"><span data-stu-id="396ad-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="396ad-113">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="396ad-113">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="396ad-114">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="396ad-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="396ad-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="396ad-115">Parent Elements</span></span>  
  
|<span data-ttu-id="396ad-116">Element</span><span class="sxs-lookup"><span data-stu-id="396ad-116">Element</span></span>|<span data-ttu-id="396ad-117">Opis</span><span class="sxs-lookup"><span data-stu-id="396ad-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="396ad-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="396ad-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="396ad-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="396ad-119">Remarks</span></span>  
 <span data-ttu-id="396ad-120">`<system.identityModel>` Dodaj sekcję do pliku konfiguracji, aby skonfigurować usługę lub aplikację do korzystania z programu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="396ad-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="396ad-121">Element jest reprezentowany <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> przez klasę. `<system.identityModel>`</span><span class="sxs-lookup"><span data-stu-id="396ad-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="396ad-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="396ad-122">Example</span></span>  
 <span data-ttu-id="396ad-123">Poniższy przykład pokazuje, jak dodać `<system.identityModel>` sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="396ad-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="396ad-124">Najpierw należy dodać sekcję konfiguracyjną i deklarację przestrzeni nazw w `<configSections>` ramach elementu.</span><span class="sxs-lookup"><span data-stu-id="396ad-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="396ad-125">Następnie można dodać `<system.IdentityModel>` element do pliku konfiguracji, aby określić co najmniej jedną konfigurację tożsamości.</span><span class="sxs-lookup"><span data-stu-id="396ad-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="396ad-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="396ad-126">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
