---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855343"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="8e518-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="8e518-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="8e518-102">Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje umożliwiające aplikacji działanie jako program kliencki, który może znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8e518-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="8e518-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8e518-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8e518-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8e518-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8e518-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="8e518-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="8e518-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dynamicEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="8e518-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e518-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e518-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e518-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8e518-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8e518-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8e518-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e518-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e518-110">Attributes</span></span>  
 <span data-ttu-id="8e518-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8e518-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e518-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e518-112">Child Elements</span></span>  
  
|<span data-ttu-id="8e518-113">Element</span><span class="sxs-lookup"><span data-stu-id="8e518-113">Element</span></span>|<span data-ttu-id="8e518-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8e518-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e518-115">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="8e518-115">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="8e518-116">Zawiera ustawienia wymagane przez aplikację do uczestnictwa w procesie odnajdowania usług jako klient.</span><span class="sxs-lookup"><span data-stu-id="8e518-116">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e518-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8e518-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8e518-118">Element</span><span class="sxs-lookup"><span data-stu-id="8e518-118">Element</span></span>|<span data-ttu-id="8e518-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8e518-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e518-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="8e518-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="8e518-121">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="8e518-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e518-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e518-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
