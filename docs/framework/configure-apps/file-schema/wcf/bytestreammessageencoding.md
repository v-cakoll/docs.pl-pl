---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 5d78aed78a5c3a10aecac53bda02d6c640bc71ae
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400585"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="53ffa-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="53ffa-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="53ffa-102">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="53ffa-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="53ffa-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="53ffa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="53ffa-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="53ffa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="53ffa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="53ffa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="53ffa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="53ffa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="53ffa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="53ffa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="53ffa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="53ffa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ffa-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="53ffa-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53ffa-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="53ffa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="53ffa-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="53ffa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53ffa-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="53ffa-112">Attributes</span></span>  
  
|<span data-ttu-id="53ffa-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="53ffa-113">Attribute</span></span>|<span data-ttu-id="53ffa-114">Opis</span><span class="sxs-lookup"><span data-stu-id="53ffa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53ffa-115">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="53ffa-115">messageVersion</span></span>|<span data-ttu-id="53ffa-116">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="53ffa-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="53ffa-117">Dla tej właściwości można ustawić tylko wartość <xref:System.ServiceModel.Channels.MessageVersion.None%2A>wersji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="53ffa-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="53ffa-118">Koder komunikatów strumienia bajtów nie obsługuje żadnych innych wersji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="53ffa-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="53ffa-119">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="53ffa-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53ffa-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="53ffa-120">Child Elements</span></span>  
  
|<span data-ttu-id="53ffa-121">Element</span><span class="sxs-lookup"><span data-stu-id="53ffa-121">Element</span></span>|<span data-ttu-id="53ffa-122">Opis</span><span class="sxs-lookup"><span data-stu-id="53ffa-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53ffa-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53ffa-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="53ffa-124">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="53ffa-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="53ffa-125">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="53ffa-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53ffa-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="53ffa-126">Parent Elements</span></span>  
  
|<span data-ttu-id="53ffa-127">Element</span><span class="sxs-lookup"><span data-stu-id="53ffa-127">Element</span></span>|<span data-ttu-id="53ffa-128">Opis</span><span class="sxs-lookup"><span data-stu-id="53ffa-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53ffa-129">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="53ffa-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="53ffa-130">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="53ffa-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53ffa-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53ffa-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="53ffa-132">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="53ffa-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="53ffa-133">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="53ffa-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="53ffa-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="53ffa-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="53ffa-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="53ffa-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="53ffa-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="53ffa-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="53ffa-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="53ffa-137">\<customBinding></span></span>](custombinding.md)
