---
title: <diagnostics>na potrzeby aktywacji
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400409"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="5d10d-102">\<diagnostics>na potrzeby aktywacji</span><span class="sxs-lookup"><span data-stu-id="5d10d-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="5d10d-103">Konfiguruje funkcje diagnostyki odbiornika Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5d10d-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="5d10d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d10d-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="5d10d-105">Typ</span><span class="sxs-lookup"><span data-stu-id="5d10d-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d10d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d10d-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5d10d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d10d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d10d-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d10d-108">Attributes</span></span>  
  
|<span data-ttu-id="5d10d-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5d10d-109">Attribute</span></span>|<span data-ttu-id="5d10d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5d10d-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="5d10d-111">Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="5d10d-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d10d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d10d-112">Child Elements</span></span>  
 <span data-ttu-id="5d10d-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="5d10d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d10d-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d10d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5d10d-115">Element</span><span class="sxs-lookup"><span data-stu-id="5d10d-115">Element</span></span>|<span data-ttu-id="5d10d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5d10d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="5d10d-117">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="5d10d-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d10d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d10d-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
