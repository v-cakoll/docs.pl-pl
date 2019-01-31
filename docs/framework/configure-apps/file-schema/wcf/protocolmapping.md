---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 6ec17457c8742fdf17208c6588e0ab70ece7c42a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268678"
---
# <a name="protocolmapping"></a><span data-ttu-id="ee7ab-101">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-101">\<protocolMapping></span></span>
<span data-ttu-id="ee7ab-102">Reprezentuje sekcję konfiguracji definiujących zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="ee7ab-103">Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, Windows Communication Foundation (WCF) analizuje skonfigurowanego mapowania i decyduje o tym, na które powiązania do użycia dla określonego na podstawie adresu.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="ee7ab-104">**\<system.serviceModel>**</span><span class="sxs-lookup"><span data-stu-id="ee7ab-104">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="ee7ab-105">&nbsp;&nbsp;**\<protocolMapping>**</span><span class="sxs-lookup"><span data-stu-id="ee7ab-105">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee7ab-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee7ab-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee7ab-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee7ab-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ee7ab-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee7ab-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee7ab-109">Attributes</span></span>  
 <span data-ttu-id="ee7ab-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee7ab-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee7ab-111">Child Elements</span></span>  
  
|<span data-ttu-id="ee7ab-112">Element</span><span class="sxs-lookup"><span data-stu-id="ee7ab-112">Element</span></span>|<span data-ttu-id="ee7ab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ee7ab-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee7ab-114">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="ee7ab-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="ee7ab-115">Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-115">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee7ab-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee7ab-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ee7ab-117">Element</span><span class="sxs-lookup"><span data-stu-id="ee7ab-117">Element</span></span>|<span data-ttu-id="ee7ab-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ee7ab-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee7ab-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ee7ab-119">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="ee7ab-120">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-120">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee7ab-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee7ab-121">Example</span></span>  
 <span data-ttu-id="ee7ab-122">W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-122">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="ee7ab-123">Możesz przesłonić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-123">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="ee7ab-124">Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracyjnym aplikacji i zmienić mapowanie schematów pojedynczy protokół.</span><span class="sxs-lookup"><span data-stu-id="ee7ab-124">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee7ab-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee7ab-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
