---
title: <add> dla <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 6197d01665d49a7c97ac9e44251abf15faf80a8f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850381"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="0f803-102">\<add> dla \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="0f803-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="0f803-103">Reprezentuje domyślne mapowanie protokołu między schematem protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniem Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0f803-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="0f803-104">Podczas tworzenia domyślnych punktów końcowych w środowisku uruchomieniowym środowisko WCF przegląda skonfigurowane mapowania i decyduje o tym, które powiązanie ma być używane dla określonego adresu.</span><span class="sxs-lookup"><span data-stu-id="0f803-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0f803-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f803-105">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f803-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0f803-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0f803-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0f803-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f803-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f803-108">Attributes</span></span>  
  
|<span data-ttu-id="0f803-109">Element</span><span class="sxs-lookup"><span data-stu-id="0f803-109">Element</span></span>|<span data-ttu-id="0f803-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0f803-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f803-111">powiązanie</span><span class="sxs-lookup"><span data-stu-id="0f803-111">binding</span></span>|<span data-ttu-id="0f803-112">Ciąg określający typ powiązania, które ma być używane dla punktu końcowego podczas domyślnego tworzenia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0f803-112">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="0f803-113">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f803-113">bindingConfiguration</span></span>|<span data-ttu-id="0f803-114">Ciąg określający nazwę sekcji konfiguracji powiązania, do której ma zostać utworzone odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0f803-114">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="0f803-115">schemat</span><span class="sxs-lookup"><span data-stu-id="0f803-115">scheme</span></span>|<span data-ttu-id="0f803-116">Schemat protokołu transportowego, który ma być używany dla domyślnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0f803-116">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f803-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f803-117">Child Elements</span></span>  
 <span data-ttu-id="0f803-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="0f803-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f803-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0f803-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0f803-120">Element</span><span class="sxs-lookup"><span data-stu-id="0f803-120">Element</span></span>|<span data-ttu-id="0f803-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0f803-121">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="0f803-122">Reprezentuje sekcję konfiguracji definiującą domyślne mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniami Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0f803-122">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f803-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f803-123">Example</span></span>  
 <span data-ttu-id="0f803-124">Poniższy przykład konfiguracji przedstawia domyślne mapowanie protokołu w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="0f803-124">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="0f803-125">To mapowanie domyślne można zastąpić na poziomie komputera, modyfikując plik Machine. config.</span><span class="sxs-lookup"><span data-stu-id="0f803-125">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="0f803-126">Lub jeśli chcesz, aby przesłonić ją tylko w ramach zakresu aplikacji, możesz zastąpić tę sekcję w pliku konfiguracji aplikacji i zmienić mapowanie poszczególnych schematów protokołu.</span><span class="sxs-lookup"><span data-stu-id="0f803-126">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f803-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f803-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
