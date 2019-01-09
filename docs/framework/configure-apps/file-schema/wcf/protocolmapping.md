---
title: '&lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: a376f1eaa7c8790cf2174335749ed3001b403967
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147307"
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="3fe15-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="3fe15-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="3fe15-103">Reprezentuje sekcję konfiguracji definiujących zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="3fe15-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="3fe15-104">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, Windows Communication Foundation (WCF) analizuje skonfigurowanego mapowania i decyduje o tym, na które powiązania do użycia dla określonego na podstawie adresu.</span><span class="sxs-lookup"><span data-stu-id="3fe15-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="3fe15-105">**\<system.serviceModel >**</span><span class="sxs-lookup"><span data-stu-id="3fe15-105">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="3fe15-106">&nbsp;&nbsp;**\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="3fe15-106">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe15-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fe15-107">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fe15-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3fe15-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3fe15-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3fe15-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fe15-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3fe15-110">Attributes</span></span>  
 <span data-ttu-id="3fe15-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="3fe15-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3fe15-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3fe15-112">Child Elements</span></span>  
  
|<span data-ttu-id="3fe15-113">Element</span><span class="sxs-lookup"><span data-stu-id="3fe15-113">Element</span></span>|<span data-ttu-id="3fe15-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3fe15-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fe15-115">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="3fe15-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="3fe15-116">Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3fe15-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3fe15-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3fe15-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3fe15-118">Element</span><span class="sxs-lookup"><span data-stu-id="3fe15-118">Element</span></span>|<span data-ttu-id="3fe15-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3fe15-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fe15-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3fe15-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="3fe15-121">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="3fe15-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3fe15-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fe15-122">Example</span></span>  
 <span data-ttu-id="3fe15-123">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="3fe15-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="3fe15-124">Możesz przesłonić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="3fe15-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="3fe15-125">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracyjnym aplikacji i zmienić mapowanie schematów pojedynczy protokół.</span><span class="sxs-lookup"><span data-stu-id="3fe15-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3fe15-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fe15-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
