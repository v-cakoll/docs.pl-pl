---
title: <add> dla <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 483ede53df13c896b88171910031dbe9793d66dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920034"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="981f4-102">\<Dodawanie > \<transportConfigurationType ></span><span class="sxs-lookup"><span data-stu-id="981f4-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="981f4-103">Ten element jest parą klucz/wartość, która identyfikuje typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="981f4-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="981f4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="981f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="981f4-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="981f4-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="981f4-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="981f4-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="981f4-107">\<add></span><span class="sxs-lookup"><span data-stu-id="981f4-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="981f4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="981f4-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="981f4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="981f4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="981f4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="981f4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="981f4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="981f4-111">Attributes</span></span>  
  
|<span data-ttu-id="981f4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="981f4-112">Attribute</span></span>|<span data-ttu-id="981f4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="981f4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="981f4-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="981f4-114">name</span></span>|<span data-ttu-id="981f4-115">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="981f4-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="981f4-116">Zawiera klucz zdefiniowany przez użytkownika, który jednoznacznie identyfikuje typ transportu.</span><span class="sxs-lookup"><span data-stu-id="981f4-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="981f4-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="981f4-117">transportConfigurationType</span></span>|<span data-ttu-id="981f4-118">Ciąg, który zawiera typ implementujący określony transport.</span><span class="sxs-lookup"><span data-stu-id="981f4-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="981f4-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="981f4-119">Child Elements</span></span>  
 <span data-ttu-id="981f4-120">Brak</span><span class="sxs-lookup"><span data-stu-id="981f4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="981f4-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="981f4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="981f4-122">Element</span><span class="sxs-lookup"><span data-stu-id="981f4-122">Element</span></span>|<span data-ttu-id="981f4-123">Opis</span><span class="sxs-lookup"><span data-stu-id="981f4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="981f4-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="981f4-124">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="981f4-125">Kolekcja typów, które implementują określony transport.</span><span class="sxs-lookup"><span data-stu-id="981f4-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="981f4-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="981f4-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="981f4-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="981f4-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="981f4-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="981f4-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
