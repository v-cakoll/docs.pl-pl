---
title: <add> dla <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926669"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="01408-102">\<Dodawanie > \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="01408-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="01408-103">Reprezentuje domyślne mapowanie protokołu między schematem protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniem Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="01408-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="01408-104">Podczas tworzenia domyślnych punktów końcowych w środowisku uruchomieniowym środowisko WCF przegląda skonfigurowane mapowania i decyduje o tym, które powiązanie ma być używane dla określonego adresu.</span><span class="sxs-lookup"><span data-stu-id="01408-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="01408-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="01408-105">\<system.serviceModel></span></span>  
<span data-ttu-id="01408-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="01408-106">\<protocolMapping></span></span>  
<span data-ttu-id="01408-107">\<add></span><span class="sxs-lookup"><span data-stu-id="01408-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01408-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="01408-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01408-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01408-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01408-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01408-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01408-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01408-111">Attributes</span></span>  
  
|<span data-ttu-id="01408-112">Element</span><span class="sxs-lookup"><span data-stu-id="01408-112">Element</span></span>|<span data-ttu-id="01408-113">Opis</span><span class="sxs-lookup"><span data-stu-id="01408-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01408-114">powiązanie</span><span class="sxs-lookup"><span data-stu-id="01408-114">binding</span></span>|<span data-ttu-id="01408-115">Ciąg określający typ powiązania, które ma być używane dla punktu końcowego podczas domyślnego tworzenia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="01408-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="01408-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="01408-116">bindingConfiguration</span></span>|<span data-ttu-id="01408-117">Ciąg określający nazwę sekcji konfiguracji powiązania, do której ma zostać utworzone odwołanie.</span><span class="sxs-lookup"><span data-stu-id="01408-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="01408-118">schemat</span><span class="sxs-lookup"><span data-stu-id="01408-118">scheme</span></span>|<span data-ttu-id="01408-119">Schemat protokołu transportowego, który ma być używany dla domyślnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="01408-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01408-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01408-120">Child Elements</span></span>  
 <span data-ttu-id="01408-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="01408-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01408-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01408-122">Parent Elements</span></span>  
  
|<span data-ttu-id="01408-123">Element</span><span class="sxs-lookup"><span data-stu-id="01408-123">Element</span></span>|<span data-ttu-id="01408-124">Opis</span><span class="sxs-lookup"><span data-stu-id="01408-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01408-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="01408-125">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="01408-126">Reprezentuje sekcję konfiguracji definiującą domyślne mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązaniami Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="01408-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="01408-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="01408-127">Example</span></span>  
 <span data-ttu-id="01408-128">Poniższy przykład konfiguracji przedstawia domyślne mapowanie protokołu w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="01408-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="01408-129">To mapowanie domyślne można zastąpić na poziomie komputera, modyfikując plik Machine. config.</span><span class="sxs-lookup"><span data-stu-id="01408-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="01408-130">Lub jeśli chcesz, aby przesłonić ją tylko w ramach zakresu aplikacji, możesz zastąpić tę sekcję w pliku konfiguracji aplikacji i zmienić mapowanie poszczególnych schematów protokołu.</span><span class="sxs-lookup"><span data-stu-id="01408-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01408-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01408-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
