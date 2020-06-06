---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400019"
---
# \<protocolMapping>
<span data-ttu-id="96877-101">Reprezentuje sekcję konfiguracyjną służącą do definiowania zestawu domyślnego mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="96877-101">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="96877-102">Podczas tworzenia domyślnych punktów końcowych w czasie wykonywania Windows Communication Foundation (WCF) przegląda skonfigurowane mapowania i decyduje o tym, które powiązanie ma być używane dla określonego adresu.</span><span class="sxs-lookup"><span data-stu-id="96877-102">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="96877-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="96877-103">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96877-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="96877-104">Attributes and Elements</span></span>  
 <span data-ttu-id="96877-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="96877-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96877-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="96877-106">Attributes</span></span>  
 <span data-ttu-id="96877-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="96877-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96877-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="96877-108">Child Elements</span></span>  
  
|<span data-ttu-id="96877-109">Element</span><span class="sxs-lookup"><span data-stu-id="96877-109">Element</span></span>|<span data-ttu-id="96877-110">Opis</span><span class="sxs-lookup"><span data-stu-id="96877-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="96877-111">Zawiera domyślne mapowanie protokołu między schematem protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniem WCF.</span><span class="sxs-lookup"><span data-stu-id="96877-111">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96877-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="96877-112">Parent Elements</span></span>  
  
|<span data-ttu-id="96877-113">Element</span><span class="sxs-lookup"><span data-stu-id="96877-113">Element</span></span>|<span data-ttu-id="96877-114">Opis</span><span class="sxs-lookup"><span data-stu-id="96877-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="96877-115">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="96877-115">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96877-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="96877-116">Example</span></span>  
 <span data-ttu-id="96877-117">Poniższy przykład konfiguracji przedstawia domyślne mapowanie protokołu w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="96877-117">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="96877-118">To mapowanie domyślne można zastąpić na poziomie komputera, modyfikując plik Machine. config.</span><span class="sxs-lookup"><span data-stu-id="96877-118">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="96877-119">Lub jeśli chcesz, aby przesłonić ją tylko w ramach zakresu aplikacji, możesz zastąpić tę sekcję w pliku konfiguracji aplikacji i zmienić mapowanie poszczególnych schematów protokołu.</span><span class="sxs-lookup"><span data-stu-id="96877-119">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96877-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96877-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
