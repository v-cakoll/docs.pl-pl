---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2d932e8a7fbe9c1457b5cea5106b69317227a21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="3015c-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="3015c-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="3015c-103">Reprezentuje sekcję konfiguracji określającą zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="3015c-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="3015c-104">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] analizuje skonfigurowanego mapowania i decyduje o tym, na których powiązanie dla określonego na podstawie adresów.</span><span class="sxs-lookup"><span data-stu-id="3015c-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="3015c-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3015c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3015c-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="3015c-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3015c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3015c-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3015c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3015c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3015c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3015c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3015c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3015c-110">Attributes</span></span>  
 <span data-ttu-id="3015c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="3015c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3015c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3015c-112">Child Elements</span></span>  
  
|<span data-ttu-id="3015c-113">Element</span><span class="sxs-lookup"><span data-stu-id="3015c-113">Element</span></span>|<span data-ttu-id="3015c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3015c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3015c-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="3015c-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="3015c-116">Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązanie WCF.</span><span class="sxs-lookup"><span data-stu-id="3015c-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3015c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3015c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3015c-118">Element</span><span class="sxs-lookup"><span data-stu-id="3015c-118">Element</span></span>|<span data-ttu-id="3015c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3015c-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3015c-120">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3015c-120">system.ServiceModel</span></span>|<span data-ttu-id="3015c-121">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3015c-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3015c-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3015c-122">Example</span></span>  
 <span data-ttu-id="3015c-123">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="3015c-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="3015c-124">Można zastąpić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="3015c-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="3015c-125">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracji aplikacji i zmień mapowanie dla poszczególnych protokołu systemów.</span><span class="sxs-lookup"><span data-stu-id="3015c-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3015c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3015c-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
