---
title: '&lt;add&gt; w &lt;transportConfigurationType&gt;'
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 5d13ef51444e1600b0cea5d55a1b5e332e440bc6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749637"
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="87562-102">&lt;add&gt; w &lt;transportConfigurationType&gt;</span><span class="sxs-lookup"><span data-stu-id="87562-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="87562-103">Ten element jest para klucza i wartości, które identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="87562-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="87562-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87562-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87562-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="87562-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="87562-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="87562-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="87562-107">\<add></span><span class="sxs-lookup"><span data-stu-id="87562-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87562-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="87562-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87562-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87562-109">Attributes and Elements</span></span>  
 <span data-ttu-id="87562-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87562-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87562-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87562-111">Attributes</span></span>  
  
|<span data-ttu-id="87562-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87562-112">Attribute</span></span>|<span data-ttu-id="87562-113">Opis</span><span class="sxs-lookup"><span data-stu-id="87562-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87562-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="87562-114">name</span></span>|<span data-ttu-id="87562-115">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="87562-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="87562-116">Zawiera klucz zdefiniowane przez użytkownika, który unikatowo identyfikuje typem transportu.</span><span class="sxs-lookup"><span data-stu-id="87562-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="87562-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="87562-117">transportConfigurationType</span></span>|<span data-ttu-id="87562-118">Ciąg, który zawiera typ, który implementuje określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="87562-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87562-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87562-119">Child Elements</span></span>  
 <span data-ttu-id="87562-120">Brak</span><span class="sxs-lookup"><span data-stu-id="87562-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87562-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87562-121">Parent Elements</span></span>  
  
|<span data-ttu-id="87562-122">Element</span><span class="sxs-lookup"><span data-stu-id="87562-122">Element</span></span>|<span data-ttu-id="87562-123">Opis</span><span class="sxs-lookup"><span data-stu-id="87562-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87562-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="87562-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="87562-125">Kolekcja typów, które implementują określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="87562-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87562-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="87562-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87562-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87562-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="87562-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="87562-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
