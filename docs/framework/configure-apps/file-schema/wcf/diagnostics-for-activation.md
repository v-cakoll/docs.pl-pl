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
ms.workload: dotnet
ms.openlocfilehash: 20b956bb58142f26fa1402f1f974b3984ed759f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="9877b-102">&lt;diagnostics&gt; w Activation</span><span class="sxs-lookup"><span data-stu-id="9877b-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="9877b-103">Konfiguruje [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funkcje diagnostyki przez odbiornik.</span><span class="sxs-lookup"><span data-stu-id="9877b-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="9877b-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="9877b-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="9877b-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="9877b-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9877b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9877b-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="9877b-107">Typ</span><span class="sxs-lookup"><span data-stu-id="9877b-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9877b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9877b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9877b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9877b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9877b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9877b-110">Attributes</span></span>  
  
|<span data-ttu-id="9877b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9877b-111">Attribute</span></span>|<span data-ttu-id="9877b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9877b-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="9877b-113">Wartość logiczna wskazująca, czy liczniki wydajności są włączone w celach diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="9877b-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9877b-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9877b-114">Child Elements</span></span>  
 <span data-ttu-id="9877b-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9877b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9877b-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9877b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9877b-117">Element</span><span class="sxs-lookup"><span data-stu-id="9877b-117">Element</span></span>|<span data-ttu-id="9877b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9877b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9877b-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="9877b-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="9877b-120">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="9877b-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9877b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9877b-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
