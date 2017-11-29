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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 769ca7b96c3671fdd1b154c99516778f7cbd542e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="36b35-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="36b35-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="36b35-103">Reprezentuje sekcję konfiguracji określającą zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="36b35-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="36b35-104">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] analizuje skonfigurowanego mapowania i decyduje o tym, na których powiązanie dla określonego na podstawie adresów.</span><span class="sxs-lookup"><span data-stu-id="36b35-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="36b35-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="36b35-105">\<system.serviceModel></span></span>  
<span data-ttu-id="36b35-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="36b35-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36b35-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="36b35-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36b35-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="36b35-108">Attributes and Elements</span></span>  
 <span data-ttu-id="36b35-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="36b35-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36b35-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="36b35-110">Attributes</span></span>  
 <span data-ttu-id="36b35-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="36b35-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36b35-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="36b35-112">Child Elements</span></span>  
  
|<span data-ttu-id="36b35-113">Element</span><span class="sxs-lookup"><span data-stu-id="36b35-113">Element</span></span>|<span data-ttu-id="36b35-114">Opis</span><span class="sxs-lookup"><span data-stu-id="36b35-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36b35-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="36b35-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="36b35-116">Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązanie WCF.</span><span class="sxs-lookup"><span data-stu-id="36b35-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36b35-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="36b35-117">Parent Elements</span></span>  
  
|<span data-ttu-id="36b35-118">Element</span><span class="sxs-lookup"><span data-stu-id="36b35-118">Element</span></span>|<span data-ttu-id="36b35-119">Opis</span><span class="sxs-lookup"><span data-stu-id="36b35-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36b35-120">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="36b35-120">system.ServiceModel</span></span>|<span data-ttu-id="36b35-121">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="36b35-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="36b35-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="36b35-122">Example</span></span>  
 <span data-ttu-id="36b35-123">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="36b35-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="36b35-124">Można zastąpić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="36b35-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="36b35-125">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracji aplikacji i zmień mapowanie dla poszczególnych protokołu systemów.</span><span class="sxs-lookup"><span data-stu-id="36b35-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36b35-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36b35-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
