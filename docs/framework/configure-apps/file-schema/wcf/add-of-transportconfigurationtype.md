---
title: <add> dla <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850318"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="5ee74-102">\<add> dla \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="5ee74-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="5ee74-103">Ten element jest parą klucz/wartość, która identyfikuje typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="5ee74-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="5ee74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ee74-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ee74-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5ee74-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5ee74-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5ee74-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ee74-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee74-107">Attributes</span></span>  
  
|<span data-ttu-id="5ee74-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5ee74-108">Attribute</span></span>|<span data-ttu-id="5ee74-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5ee74-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ee74-110">name</span><span class="sxs-lookup"><span data-stu-id="5ee74-110">name</span></span>|<span data-ttu-id="5ee74-111">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="5ee74-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="5ee74-112">Zawiera klucz zdefiniowany przez użytkownika, który jednoznacznie identyfikuje typ transportu.</span><span class="sxs-lookup"><span data-stu-id="5ee74-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="5ee74-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="5ee74-113">transportConfigurationType</span></span>|<span data-ttu-id="5ee74-114">Ciąg, który zawiera typ implementujący określony transport.</span><span class="sxs-lookup"><span data-stu-id="5ee74-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ee74-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5ee74-115">Child Elements</span></span>  
 <span data-ttu-id="5ee74-116">Brak</span><span class="sxs-lookup"><span data-stu-id="5ee74-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ee74-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5ee74-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5ee74-118">Element</span><span class="sxs-lookup"><span data-stu-id="5ee74-118">Element</span></span>|<span data-ttu-id="5ee74-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5ee74-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="5ee74-120">Kolekcja typów, które implementują określony transport.</span><span class="sxs-lookup"><span data-stu-id="5ee74-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5ee74-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ee74-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="5ee74-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ee74-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="5ee74-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="5ee74-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
