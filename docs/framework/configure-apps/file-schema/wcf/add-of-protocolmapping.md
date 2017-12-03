---
title: '&lt;add&gt; w &lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 255cd8518bd9c6c6c199c75aa32ca086c801d23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="b622d-102">&lt;add&gt; w &lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="b622d-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="b622d-103">Reprezentuje domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] powiązania.</span><span class="sxs-lookup"><span data-stu-id="b622d-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span> <span data-ttu-id="b622d-104">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analizuje skonfigurowanego mapowania i decyduje o tym, na których powiązanie dla określonego na podstawie adresów.</span><span class="sxs-lookup"><span data-stu-id="b622d-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="b622d-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b622d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b622d-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="b622d-106">\<protocolMapping></span></span>  
<span data-ttu-id="b622d-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="b622d-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b622d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b622d-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b622d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b622d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b622d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b622d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b622d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b622d-111">Attributes</span></span>  
  
|<span data-ttu-id="b622d-112">Element</span><span class="sxs-lookup"><span data-stu-id="b622d-112">Element</span></span>|<span data-ttu-id="b622d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b622d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b622d-114">powiązanie</span><span class="sxs-lookup"><span data-stu-id="b622d-114">binding</span></span>|<span data-ttu-id="b622d-115">Ciąg określający typ powiązania stosowanego dla punktu końcowego podczas domyślnego tworzenia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b622d-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="b622d-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b622d-116">bindingConfiguration</span></span>|<span data-ttu-id="b622d-117">Ciąg określający nazwę sekcji konfiguracji powiązania aby odwoływać.</span><span class="sxs-lookup"><span data-stu-id="b622d-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="b622d-118">schemat</span><span class="sxs-lookup"><span data-stu-id="b622d-118">scheme</span></span>|<span data-ttu-id="b622d-119">Schemat transportu protokołu używanego do domyślnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b622d-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b622d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b622d-120">Child Elements</span></span>  
 <span data-ttu-id="b622d-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="b622d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b622d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b622d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b622d-123">Element</span><span class="sxs-lookup"><span data-stu-id="b622d-123">Element</span></span>|<span data-ttu-id="b622d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b622d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b622d-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="b622d-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="b622d-126">Reprezentuje sekcję konfiguracji określającą domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] powiązania.</span><span class="sxs-lookup"><span data-stu-id="b622d-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b622d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="b622d-127">Example</span></span>  
 <span data-ttu-id="b622d-128">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="b622d-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="b622d-129">Można zastąpić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="b622d-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="b622d-130">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracji aplikacji i zmień mapowanie dla poszczególnych protokołu systemów.</span><span class="sxs-lookup"><span data-stu-id="b622d-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b622d-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b622d-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
