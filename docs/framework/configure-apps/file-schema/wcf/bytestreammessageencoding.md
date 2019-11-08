---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739059"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="ff9ef-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="ff9ef-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="ff9ef-102">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="ff9ef-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ff9ef-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff9ef-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ff9ef-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff9ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="ff9ef-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ff9ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="ff9ef-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="ff9ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="ff9ef-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ff9ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="ff9ef-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9ef-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff9ef-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff9ef-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff9ef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff9ef-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff9ef-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff9ef-112">Attributes</span></span>  
  
|<span data-ttu-id="ff9ef-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ff9ef-113">Attribute</span></span>|<span data-ttu-id="ff9ef-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ff9ef-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff9ef-115">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="ff9ef-115">messageVersion</span></span>|<span data-ttu-id="ff9ef-116">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="ff9ef-117">Dla tej właściwości można ustawić tylko wartość wersji komunikatu <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="ff9ef-118">Koder komunikatów strumienia bajtów nie obsługuje żadnych innych wersji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="ff9ef-119">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff9ef-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff9ef-120">Child Elements</span></span>  
  
|<span data-ttu-id="ff9ef-121">Element</span><span class="sxs-lookup"><span data-stu-id="ff9ef-121">Element</span></span>|<span data-ttu-id="ff9ef-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ff9ef-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff9ef-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ff9ef-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="ff9ef-124">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ff9ef-125">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff9ef-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff9ef-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ff9ef-127">Element</span><span class="sxs-lookup"><span data-stu-id="ff9ef-127">Element</span></span>|<span data-ttu-id="ff9ef-128">Opis</span><span class="sxs-lookup"><span data-stu-id="ff9ef-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff9ef-129">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="ff9ef-129">\<binding></span></span>](bindings.md)|<span data-ttu-id="ff9ef-130">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ff9ef-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff9ef-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff9ef-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="ff9ef-132">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="ff9ef-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="ff9ef-133">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="ff9ef-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="ff9ef-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ff9ef-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ff9ef-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="ff9ef-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ff9ef-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ff9ef-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ff9ef-137">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="ff9ef-137">\<customBinding></span></span>](custombinding.md)
