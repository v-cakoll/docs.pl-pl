---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251793"
---
# \<system.identityModel>
<span data-ttu-id="d2e90-102">Zapewnia konfigurację umożliwiającą włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d2e90-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="d2e90-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2e90-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2e90-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2e90-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d2e90-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2e90-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2e90-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2e90-106">Attributes</span></span>  
 <span data-ttu-id="d2e90-107">Brak</span><span class="sxs-lookup"><span data-stu-id="d2e90-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d2e90-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2e90-108">Child Elements</span></span>  
  
|<span data-ttu-id="d2e90-109">Element</span><span class="sxs-lookup"><span data-stu-id="d2e90-109">Element</span></span>|<span data-ttu-id="d2e90-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d2e90-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="d2e90-111">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="d2e90-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2e90-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2e90-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d2e90-113">Element</span><span class="sxs-lookup"><span data-stu-id="d2e90-113">Element</span></span>|<span data-ttu-id="d2e90-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d2e90-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="d2e90-115">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2e90-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2e90-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2e90-116">Remarks</span></span>  
 <span data-ttu-id="d2e90-117">Dodaj `<system.identityModel>` sekcję do pliku konfiguracji, aby skonfigurować usługę lub aplikację do korzystania z programu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="d2e90-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="d2e90-118">`<system.identityModel>`Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> klasę.</span><span class="sxs-lookup"><span data-stu-id="d2e90-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2e90-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2e90-119">Example</span></span>  
 <span data-ttu-id="d2e90-120">Poniższy przykład pokazuje, jak dodać `<system.identityModel>` sekcję do pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2e90-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="d2e90-121">Najpierw należy dodać sekcję konfiguracyjną i deklarację przestrzeni nazw w ramach `<configSections>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d2e90-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="d2e90-122">Następnie można dodać `<system.IdentityModel>` element do pliku konfiguracji, aby określić co najmniej jedną konfigurację tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d2e90-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2e90-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2e90-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
