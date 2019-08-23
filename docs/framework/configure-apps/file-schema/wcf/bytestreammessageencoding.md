---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: b11f472c0e33003e50be4b45bb49196c64ecb70d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919731"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="94075-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="94075-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="94075-102">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="94075-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="94075-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="94075-103">\<system.serviceModel></span></span>  
<span data-ttu-id="94075-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="94075-104">\<bindings></span></span>  
<span data-ttu-id="94075-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="94075-105">\<customBinding></span></span>  
<span data-ttu-id="94075-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="94075-106">\<binding></span></span>  
<span data-ttu-id="94075-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="94075-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94075-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="94075-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94075-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="94075-109">Attributes and Elements</span></span>  
 <span data-ttu-id="94075-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="94075-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94075-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94075-111">Attributes</span></span>  
  
|<span data-ttu-id="94075-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="94075-112">Attribute</span></span>|<span data-ttu-id="94075-113">Opis</span><span class="sxs-lookup"><span data-stu-id="94075-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94075-114">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="94075-114">messageVersion</span></span>|<span data-ttu-id="94075-115">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="94075-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="94075-116">Dla tej właściwości można ustawić tylko wartość <xref:System.ServiceModel.Channels.MessageVersion.None%2A>wersji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="94075-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="94075-117">Koder komunikatów strumienia bajtów nie obsługuje żadnych innych wersji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="94075-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="94075-118">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="94075-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94075-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94075-119">Child Elements</span></span>  
  
|<span data-ttu-id="94075-120">Element</span><span class="sxs-lookup"><span data-stu-id="94075-120">Element</span></span>|<span data-ttu-id="94075-121">Opis</span><span class="sxs-lookup"><span data-stu-id="94075-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94075-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="94075-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="94075-123">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="94075-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="94075-124">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="94075-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94075-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="94075-125">Parent Elements</span></span>  
  
|<span data-ttu-id="94075-126">Element</span><span class="sxs-lookup"><span data-stu-id="94075-126">Element</span></span>|<span data-ttu-id="94075-127">Opis</span><span class="sxs-lookup"><span data-stu-id="94075-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94075-128">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="94075-128">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="94075-129">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="94075-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94075-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94075-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="94075-131">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="94075-131">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="94075-132">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="94075-132">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="94075-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="94075-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="94075-134">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="94075-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="94075-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="94075-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="94075-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="94075-136">\<customBinding></span></span>](custombinding.md)
