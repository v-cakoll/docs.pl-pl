---
title: <diagnostics>na potrzeby aktywacji
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919218"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="48cd5-102">\<> diagnostyki na potrzeby aktywacji</span><span class="sxs-lookup"><span data-stu-id="48cd5-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="48cd5-103">Konfiguruje funkcje diagnostyki odbiornika Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="48cd5-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="48cd5-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="48cd5-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="48cd5-105">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="48cd5-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cd5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="48cd5-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="48cd5-107">Typ</span><span class="sxs-lookup"><span data-stu-id="48cd5-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48cd5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="48cd5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="48cd5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="48cd5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48cd5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="48cd5-110">Attributes</span></span>  
  
|<span data-ttu-id="48cd5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="48cd5-111">Attribute</span></span>|<span data-ttu-id="48cd5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="48cd5-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="48cd5-113">Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="48cd5-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48cd5-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="48cd5-114">Child Elements</span></span>  
 <span data-ttu-id="48cd5-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="48cd5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48cd5-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="48cd5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="48cd5-117">Element</span><span class="sxs-lookup"><span data-stu-id="48cd5-117">Element</span></span>|<span data-ttu-id="48cd5-118">Opis</span><span class="sxs-lookup"><span data-stu-id="48cd5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48cd5-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="48cd5-119">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="48cd5-120">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="48cd5-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48cd5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48cd5-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
