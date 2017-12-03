---
title: '&lt;diagnostics&gt; w Activation'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1610c77125d2820e3adc06b3c37177058c85abdd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="d4e4d-102">&lt;diagnostics&gt; w Activation</span><span class="sxs-lookup"><span data-stu-id="d4e4d-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="d4e4d-103">Konfiguruje [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funkcje diagnostyki przez odbiornik.</span><span class="sxs-lookup"><span data-stu-id="d4e4d-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="d4e4d-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d4e4d-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="d4e4d-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="d4e4d-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e4d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4e4d-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="d4e4d-107">Typ</span><span class="sxs-lookup"><span data-stu-id="d4e4d-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4e4d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4e4d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d4e4d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4e4d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4e4d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4e4d-110">Attributes</span></span>  
  
|<span data-ttu-id="d4e4d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4e4d-111">Attribute</span></span>|<span data-ttu-id="d4e4d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e4d-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="d4e4d-113">Wartość logiczna wskazująca, czy liczniki wydajności są włączone w celach diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="d4e4d-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4e4d-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4e4d-114">Child Elements</span></span>  
 <span data-ttu-id="d4e4d-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="d4e4d-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4e4d-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4e4d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d4e4d-117">Element</span><span class="sxs-lookup"><span data-stu-id="d4e4d-117">Element</span></span>|<span data-ttu-id="d4e4d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e4d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e4d-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d4e4d-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="d4e4d-120">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="d4e4d-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4e4d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4e4d-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
