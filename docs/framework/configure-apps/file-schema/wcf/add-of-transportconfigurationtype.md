---
title: <add> dla <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: c71a58b13e89bedb5eed24d784c82fb1525f7625
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701440"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="2f974-102">\<add> of \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="2f974-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="2f974-103">Ten element jest para klucza i wartości, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="2f974-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="2f974-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2f974-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2f974-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="2f974-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="2f974-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="2f974-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="2f974-107">\<add></span><span class="sxs-lookup"><span data-stu-id="2f974-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f974-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f974-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f974-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2f974-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2f974-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f974-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f974-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2f974-111">Attributes</span></span>  
  
|<span data-ttu-id="2f974-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2f974-112">Attribute</span></span>|<span data-ttu-id="2f974-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2f974-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f974-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="2f974-114">name</span></span>|<span data-ttu-id="2f974-115">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="2f974-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="2f974-116">Zawiera klucz zdefiniowanych przez użytkownika, który unikatowo identyfikuje typ transportu.</span><span class="sxs-lookup"><span data-stu-id="2f974-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="2f974-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="2f974-117">transportConfigurationType</span></span>|<span data-ttu-id="2f974-118">Ciąg, który zawiera typ, który implementuje określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="2f974-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f974-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2f974-119">Child Elements</span></span>  
 <span data-ttu-id="2f974-120">Brak</span><span class="sxs-lookup"><span data-stu-id="2f974-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f974-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2f974-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2f974-122">Element</span><span class="sxs-lookup"><span data-stu-id="2f974-122">Element</span></span>|<span data-ttu-id="2f974-123">Opis</span><span class="sxs-lookup"><span data-stu-id="2f974-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f974-124">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="2f974-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="2f974-125">Kolekcja typów implementujących określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="2f974-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f974-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f974-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="2f974-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f974-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="2f974-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="2f974-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
