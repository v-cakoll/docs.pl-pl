---
title: <diagnostics> w celu aktywacji
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: ac235b9a3c125cd3fe63ccd899e2ff92d4d3f31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278459"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="c8356-102">\<Diagnostyka > w celu aktywacji</span><span class="sxs-lookup"><span data-stu-id="c8356-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="c8356-103">Umożliwia skonfigurowanie funkcji diagnostyki odbiornika usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c8356-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="c8356-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="c8356-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="c8356-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="c8356-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8356-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8356-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="c8356-107">Typ</span><span class="sxs-lookup"><span data-stu-id="c8356-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8356-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8356-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c8356-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8356-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8356-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8356-110">Attributes</span></span>  
  
|<span data-ttu-id="c8356-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c8356-111">Attribute</span></span>|<span data-ttu-id="c8356-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c8356-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="c8356-113">Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="c8356-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8356-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8356-114">Child Elements</span></span>  
 <span data-ttu-id="c8356-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="c8356-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8356-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8356-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c8356-117">Element</span><span class="sxs-lookup"><span data-stu-id="c8356-117">Element</span></span>|<span data-ttu-id="c8356-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c8356-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8356-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="c8356-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="c8356-120">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="c8356-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8356-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8356-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
