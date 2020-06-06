---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855413"
---
# \<discoveryClientSettings>
<span data-ttu-id="9e076-101">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="9e076-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9e076-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e076-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e076-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9e076-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9e076-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9e076-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e076-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9e076-105">Attributes</span></span>  
  
|<span data-ttu-id="9e076-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9e076-106">Attribute</span></span>|<span data-ttu-id="9e076-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9e076-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e076-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="9e076-108">discoveryEndpoint</span></span>|<span data-ttu-id="9e076-109">Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9e076-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e076-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9e076-110">Child Elements</span></span>  
  
|<span data-ttu-id="9e076-111">Element</span><span class="sxs-lookup"><span data-stu-id="9e076-111">Element</span></span>|<span data-ttu-id="9e076-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9e076-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="9e076-113">Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="9e076-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="9e076-114">Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).</span><span class="sxs-lookup"><span data-stu-id="9e076-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e076-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9e076-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9e076-116">Element</span><span class="sxs-lookup"><span data-stu-id="9e076-116">Element</span></span>|<span data-ttu-id="9e076-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9e076-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="9e076-118">Definiuje standardowy punkt końcowy, który zawiera informacje umożliwiające aplikacji działanie jako program kliencki, który może znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9e076-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e076-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e076-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
