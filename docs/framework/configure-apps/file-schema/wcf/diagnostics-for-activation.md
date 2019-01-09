---
title: '&lt;diagnostics&gt; w Activation'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 28f051a7ab06dbc1b40f804c56071818eb37e88b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144980"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="b753f-102">&lt;diagnostics&gt; w Activation</span><span class="sxs-lookup"><span data-stu-id="b753f-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="b753f-103">Umożliwia skonfigurowanie funkcji diagnostyki odbiornika usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b753f-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="b753f-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b753f-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="b753f-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="b753f-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b753f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b753f-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="b753f-107">Typ</span><span class="sxs-lookup"><span data-stu-id="b753f-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b753f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b753f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b753f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b753f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b753f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b753f-110">Attributes</span></span>  
  
|<span data-ttu-id="b753f-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b753f-111">Attribute</span></span>|<span data-ttu-id="b753f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b753f-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="b753f-113">Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="b753f-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b753f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b753f-114">Child Elements</span></span>  
 <span data-ttu-id="b753f-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="b753f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b753f-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b753f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b753f-117">Element</span><span class="sxs-lookup"><span data-stu-id="b753f-117">Element</span></span>|<span data-ttu-id="b753f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b753f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b753f-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b753f-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="b753f-120">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="b753f-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b753f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b753f-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
