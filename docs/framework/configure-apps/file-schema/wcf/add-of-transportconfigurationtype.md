---
title: <add> dla <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850318"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="18f2d-102">\<Dodawanie > \<transportConfigurationType ></span><span class="sxs-lookup"><span data-stu-id="18f2d-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="18f2d-103">Ten element jest parą klucz/wartość, która identyfikuje typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="18f2d-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
<span data-ttu-id="18f2d-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="18f2d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="18f2d-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="18f2d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="18f2d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="18f2d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="18f2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<transportConfigurationTypes >** ](transportconfigurationtypes.md)</span><span class="sxs-lookup"><span data-stu-id="18f2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)</span></span>\
<span data-ttu-id="18f2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="18f2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f2d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="18f2d-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18f2d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="18f2d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18f2d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="18f2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18f2d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="18f2d-112">Attributes</span></span>  
  
|<span data-ttu-id="18f2d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="18f2d-113">Attribute</span></span>|<span data-ttu-id="18f2d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="18f2d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18f2d-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="18f2d-115">name</span></span>|<span data-ttu-id="18f2d-116">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="18f2d-116">Required String attribute.</span></span><br /><br /> <span data-ttu-id="18f2d-117">Zawiera klucz zdefiniowany przez użytkownika, który jednoznacznie identyfikuje typ transportu.</span><span class="sxs-lookup"><span data-stu-id="18f2d-117">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="18f2d-118">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="18f2d-118">transportConfigurationType</span></span>|<span data-ttu-id="18f2d-119">Ciąg, który zawiera typ implementujący określony transport.</span><span class="sxs-lookup"><span data-stu-id="18f2d-119">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18f2d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="18f2d-120">Child Elements</span></span>  
 <span data-ttu-id="18f2d-121">Brak</span><span class="sxs-lookup"><span data-stu-id="18f2d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18f2d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="18f2d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="18f2d-123">Element</span><span class="sxs-lookup"><span data-stu-id="18f2d-123">Element</span></span>|<span data-ttu-id="18f2d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="18f2d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18f2d-125">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="18f2d-125">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="18f2d-126">Kolekcja typów, które implementują określony transport.</span><span class="sxs-lookup"><span data-stu-id="18f2d-126">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="18f2d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="18f2d-127">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="18f2d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18f2d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="18f2d-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="18f2d-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
