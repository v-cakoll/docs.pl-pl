---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855343"
---
# \<dynamicEndpoint>
<span data-ttu-id="e8b31-101">Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje umożliwiające aplikacji działanie jako program kliencki, który może znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e8b31-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="e8b31-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8b31-102">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8b31-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8b31-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e8b31-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8b31-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8b31-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8b31-105">Attributes</span></span>  
 <span data-ttu-id="e8b31-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="e8b31-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8b31-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8b31-107">Child Elements</span></span>  
  
|<span data-ttu-id="e8b31-108">Element</span><span class="sxs-lookup"><span data-stu-id="e8b31-108">Element</span></span>|<span data-ttu-id="e8b31-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b31-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="e8b31-110">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="e8b31-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8b31-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8b31-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e8b31-112">Element</span><span class="sxs-lookup"><span data-stu-id="e8b31-112">Element</span></span>|<span data-ttu-id="e8b31-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b31-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="e8b31-114">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="e8b31-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8b31-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8b31-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
