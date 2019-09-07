---
title: <diagnostics>na potrzeby aktywacji
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400409"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="a7273-102">\<> diagnostyki na potrzeby aktywacji</span><span class="sxs-lookup"><span data-stu-id="a7273-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="a7273-103">Konfiguruje funkcje diagnostyki odbiornika Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7273-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
<span data-ttu-id="a7273-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7273-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7273-105">&nbsp;&nbsp;[ **\<> System. serviceModel. Activation**](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="a7273-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="a7273-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> diagnostyki**</span><span class="sxs-lookup"><span data-stu-id="a7273-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7273-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7273-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="a7273-108">Typ</span><span class="sxs-lookup"><span data-stu-id="a7273-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7273-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a7273-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7273-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a7273-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7273-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a7273-111">Attributes</span></span>  
  
|<span data-ttu-id="a7273-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7273-112">Attribute</span></span>|<span data-ttu-id="a7273-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a7273-113">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="a7273-114">Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="a7273-114">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7273-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a7273-115">Child Elements</span></span>  
 <span data-ttu-id="a7273-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="a7273-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7273-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a7273-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a7273-118">Element</span><span class="sxs-lookup"><span data-stu-id="a7273-118">Element</span></span>|<span data-ttu-id="a7273-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a7273-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7273-120">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="a7273-120">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="a7273-121">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="a7273-121">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7273-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7273-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
