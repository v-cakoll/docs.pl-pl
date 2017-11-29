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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 29f2e56dd18da9dc3ce3206f5c3c80f4a47a7ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="80214-102">&lt;diagnostics&gt; w Activation</span><span class="sxs-lookup"><span data-stu-id="80214-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="80214-103">Konfiguruje [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funkcje diagnostyki przez odbiornik.</span><span class="sxs-lookup"><span data-stu-id="80214-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="80214-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="80214-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="80214-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="80214-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80214-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="80214-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="80214-107">Typ</span><span class="sxs-lookup"><span data-stu-id="80214-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80214-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80214-108">Attributes and Elements</span></span>  
 <span data-ttu-id="80214-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80214-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80214-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80214-110">Attributes</span></span>  
  
|<span data-ttu-id="80214-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="80214-111">Attribute</span></span>|<span data-ttu-id="80214-112">Opis</span><span class="sxs-lookup"><span data-stu-id="80214-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="80214-113">Wartość logiczna wskazująca, czy liczniki wydajności są włączone w celach diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="80214-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80214-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80214-114">Child Elements</span></span>  
 <span data-ttu-id="80214-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="80214-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80214-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80214-116">Parent Elements</span></span>  
  
|<span data-ttu-id="80214-117">Element</span><span class="sxs-lookup"><span data-stu-id="80214-117">Element</span></span>|<span data-ttu-id="80214-118">Opis</span><span class="sxs-lookup"><span data-stu-id="80214-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80214-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="80214-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="80214-120">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="80214-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80214-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80214-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
