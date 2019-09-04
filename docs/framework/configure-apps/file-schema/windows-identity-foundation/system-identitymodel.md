---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251793"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="aa20a-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="aa20a-102">\<system.identityModel></span></span>
<span data-ttu-id="aa20a-103">Zapewnia konfigurację umożliwiającą włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="aa20a-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
<span data-ttu-id="aa20a-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="aa20a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aa20a-105">&nbsp;&nbsp; **\<> System. identityModel**</span><span class="sxs-lookup"><span data-stu-id="aa20a-105">&nbsp;&nbsp;**\<system.identityModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa20a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa20a-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa20a-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aa20a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="aa20a-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aa20a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa20a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aa20a-109">Attributes</span></span>  
 <span data-ttu-id="aa20a-110">Brak</span><span class="sxs-lookup"><span data-stu-id="aa20a-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aa20a-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aa20a-111">Child Elements</span></span>  
  
|<span data-ttu-id="aa20a-112">Element</span><span class="sxs-lookup"><span data-stu-id="aa20a-112">Element</span></span>|<span data-ttu-id="aa20a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="aa20a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa20a-114">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="aa20a-114">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="aa20a-115">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="aa20a-115">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa20a-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aa20a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="aa20a-117">Element</span><span class="sxs-lookup"><span data-stu-id="aa20a-117">Element</span></span>|<span data-ttu-id="aa20a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="aa20a-118">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="aa20a-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa20a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa20a-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa20a-120">Remarks</span></span>  
 <span data-ttu-id="aa20a-121">`<system.identityModel>` Dodaj sekcję do pliku konfiguracji, aby skonfigurować usługę lub aplikację do korzystania z programu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="aa20a-121">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="aa20a-122">Element jest reprezentowany <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> przez klasę. `<system.identityModel>`</span><span class="sxs-lookup"><span data-stu-id="aa20a-122">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa20a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa20a-123">Example</span></span>  
 <span data-ttu-id="aa20a-124">Poniższy przykład pokazuje, jak dodać `<system.identityModel>` sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aa20a-124">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="aa20a-125">Najpierw należy dodać sekcję konfiguracyjną i deklarację przestrzeni nazw w `<configSections>` ramach elementu.</span><span class="sxs-lookup"><span data-stu-id="aa20a-125">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="aa20a-126">Następnie można dodać `<system.IdentityModel>` element do pliku konfiguracji, aby określić co najmniej jedną konfigurację tożsamości.</span><span class="sxs-lookup"><span data-stu-id="aa20a-126">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa20a-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa20a-127">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
