---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739035"
---
# \<discoveryClient>
<span data-ttu-id="afa2c-101">Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="afa2c-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="afa2c-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="afa2c-102">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afa2c-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="afa2c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="afa2c-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="afa2c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afa2c-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="afa2c-105">Attributes</span></span>  
  
|<span data-ttu-id="afa2c-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="afa2c-106">Attribute</span></span>|<span data-ttu-id="afa2c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="afa2c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afa2c-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="afa2c-108">discoveryEndpoint</span></span>|<span data-ttu-id="afa2c-109">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="afa2c-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afa2c-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="afa2c-110">Child Elements</span></span>  
  
|<span data-ttu-id="afa2c-111">Element</span><span class="sxs-lookup"><span data-stu-id="afa2c-111">Element</span></span>|<span data-ttu-id="afa2c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="afa2c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="afa2c-113">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="afa2c-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="afa2c-114">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="afa2c-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afa2c-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="afa2c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="afa2c-116">Element</span><span class="sxs-lookup"><span data-stu-id="afa2c-116">Element</span></span>|<span data-ttu-id="afa2c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="afa2c-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="afa2c-118">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="afa2c-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afa2c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afa2c-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
