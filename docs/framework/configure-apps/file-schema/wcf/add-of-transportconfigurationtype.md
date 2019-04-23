---
title: <add> dla <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: c71a58b13e89bedb5eed24d784c82fb1525f7625
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126727"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="7e42b-102">\<add> of \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="7e42b-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="7e42b-103">Ten element jest para klucza i wartości, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="7e42b-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="7e42b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7e42b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e42b-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="7e42b-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="7e42b-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="7e42b-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="7e42b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="7e42b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e42b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e42b-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e42b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7e42b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7e42b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7e42b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e42b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7e42b-111">Attributes</span></span>  
  
|<span data-ttu-id="7e42b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7e42b-112">Attribute</span></span>|<span data-ttu-id="7e42b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7e42b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e42b-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="7e42b-114">name</span></span>|<span data-ttu-id="7e42b-115">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="7e42b-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="7e42b-116">Zawiera klucz zdefiniowanych przez użytkownika, który unikatowo identyfikuje typ transportu.</span><span class="sxs-lookup"><span data-stu-id="7e42b-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="7e42b-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="7e42b-117">transportConfigurationType</span></span>|<span data-ttu-id="7e42b-118">Ciąg, który zawiera typ, który implementuje określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="7e42b-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e42b-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7e42b-119">Child Elements</span></span>  
 <span data-ttu-id="7e42b-120">Brak</span><span class="sxs-lookup"><span data-stu-id="7e42b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e42b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7e42b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7e42b-122">Element</span><span class="sxs-lookup"><span data-stu-id="7e42b-122">Element</span></span>|<span data-ttu-id="7e42b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="7e42b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e42b-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="7e42b-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="7e42b-125">Kolekcja typów implementujących określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="7e42b-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7e42b-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e42b-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="7e42b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e42b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="7e42b-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="7e42b-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
