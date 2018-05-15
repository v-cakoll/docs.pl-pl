---
title: '&lt;ProtocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 4afdaaa62c1ac3241eb7382d0995bed51bde73e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="26103-102">&lt;ProtocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="26103-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="26103-103">Reprezentuje sekcję konfiguracji określającą zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="26103-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="26103-104">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, Windows Communication Foundation (WCF) przegląda skonfigurowanego mapowania i decyduje o tym, na których powiązanie dla określonego na podstawie adresów.</span><span class="sxs-lookup"><span data-stu-id="26103-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="26103-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26103-105">\<system.serviceModel></span></span>  
<span data-ttu-id="26103-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="26103-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26103-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="26103-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26103-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="26103-108">Attributes and Elements</span></span>  
 <span data-ttu-id="26103-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="26103-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26103-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26103-110">Attributes</span></span>  
 <span data-ttu-id="26103-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="26103-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="26103-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="26103-112">Child Elements</span></span>  
  
|<span data-ttu-id="26103-113">Element</span><span class="sxs-lookup"><span data-stu-id="26103-113">Element</span></span>|<span data-ttu-id="26103-114">Opis</span><span class="sxs-lookup"><span data-stu-id="26103-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26103-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="26103-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="26103-116">Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązanie WCF.</span><span class="sxs-lookup"><span data-stu-id="26103-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26103-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="26103-117">Parent Elements</span></span>  
  
|<span data-ttu-id="26103-118">Element</span><span class="sxs-lookup"><span data-stu-id="26103-118">Element</span></span>|<span data-ttu-id="26103-119">Opis</span><span class="sxs-lookup"><span data-stu-id="26103-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26103-120">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="26103-120">system.ServiceModel</span></span>|<span data-ttu-id="26103-121">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="26103-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="26103-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="26103-122">Example</span></span>  
 <span data-ttu-id="26103-123">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="26103-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="26103-124">Można zastąpić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="26103-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="26103-125">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracji aplikacji i zmień mapowanie dla poszczególnych protokołu systemów.</span><span class="sxs-lookup"><span data-stu-id="26103-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26103-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26103-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
