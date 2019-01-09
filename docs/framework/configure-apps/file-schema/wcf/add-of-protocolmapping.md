---
title: '&lt;add&gt; w &lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: e21c3ca665d6a75394d70da43ec2044e00f16429
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145487"
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="15bd1-102">&lt;add&gt; w &lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="15bd1-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="15bd1-103">Reprezentuje domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) a powiązaniem Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15bd1-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="15bd1-104">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, WCF analizuje skonfigurowanego mapowania i decyduje o tym, na które powiązania do użycia dla określonego na podstawie adresu.</span><span class="sxs-lookup"><span data-stu-id="15bd1-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="15bd1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="15bd1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="15bd1-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="15bd1-106">\<protocolMapping></span></span>  
<span data-ttu-id="15bd1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="15bd1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bd1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="15bd1-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15bd1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="15bd1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15bd1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="15bd1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15bd1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="15bd1-111">Attributes</span></span>  
  
|<span data-ttu-id="15bd1-112">Element</span><span class="sxs-lookup"><span data-stu-id="15bd1-112">Element</span></span>|<span data-ttu-id="15bd1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15bd1-114">powiązanie</span><span class="sxs-lookup"><span data-stu-id="15bd1-114">binding</span></span>|<span data-ttu-id="15bd1-115">Ciąg określający typ powiązania stosowanego dla punktu końcowego podczas domyślnego tworzenia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="15bd1-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="15bd1-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="15bd1-116">bindingConfiguration</span></span>|<span data-ttu-id="15bd1-117">Ciąg określający nazwę sekcji konfiguracji powiązania można odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="15bd1-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="15bd1-118">schemat</span><span class="sxs-lookup"><span data-stu-id="15bd1-118">scheme</span></span>|<span data-ttu-id="15bd1-119">Schematem protokołu transportu, która ma być używany dla domyślnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="15bd1-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15bd1-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="15bd1-120">Child Elements</span></span>  
 <span data-ttu-id="15bd1-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="15bd1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15bd1-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15bd1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="15bd1-123">Element</span><span class="sxs-lookup"><span data-stu-id="15bd1-123">Element</span></span>|<span data-ttu-id="15bd1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="15bd1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15bd1-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="15bd1-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="15bd1-126">Reprezentuje sekcję konfiguracji do definiowania domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązania Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15bd1-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="15bd1-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="15bd1-127">Example</span></span>  
 <span data-ttu-id="15bd1-128">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="15bd1-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="15bd1-129">Możesz przesłonić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="15bd1-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="15bd1-130">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracyjnym aplikacji i zmienić mapowanie schematów pojedynczy protokół.</span><span class="sxs-lookup"><span data-stu-id="15bd1-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="15bd1-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15bd1-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
