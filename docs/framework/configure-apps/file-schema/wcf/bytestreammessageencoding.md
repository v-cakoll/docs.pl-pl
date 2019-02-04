---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: c8dfd6824877d6f9e5b089a538cce35ffe51320b
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674285"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="731a4-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="731a4-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="731a4-102">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="731a4-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="731a4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="731a4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="731a4-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="731a4-104">\<bindings></span></span>  
<span data-ttu-id="731a4-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="731a4-105">\<customBinding></span></span>  
<span data-ttu-id="731a4-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="731a4-106">\<binding></span></span>  
<span data-ttu-id="731a4-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="731a4-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="731a4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="731a4-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="731a4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="731a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="731a4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="731a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="731a4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="731a4-111">Attributes</span></span>  
  
|<span data-ttu-id="731a4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="731a4-112">Attribute</span></span>|<span data-ttu-id="731a4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="731a4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="731a4-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="731a4-114">messageVersion</span></span>|<span data-ttu-id="731a4-115">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="731a4-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="731a4-116">Tę właściwość można ustawić tylko wartość wersji wiadomości <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="731a4-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="731a4-117">Koder komunikatów strumień bajtów nie obsługuje inne wersje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="731a4-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="731a4-118">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="731a4-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="731a4-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="731a4-119">Child Elements</span></span>  
  
|<span data-ttu-id="731a4-120">Element</span><span class="sxs-lookup"><span data-stu-id="731a4-120">Element</span></span>|<span data-ttu-id="731a4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="731a4-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="731a4-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="731a4-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="731a4-123">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="731a4-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="731a4-124">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="731a4-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="731a4-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="731a4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="731a4-126">Element</span><span class="sxs-lookup"><span data-stu-id="731a4-126">Element</span></span>|<span data-ttu-id="731a4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="731a4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="731a4-128">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="731a4-128">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="731a4-129">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="731a4-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="731a4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="731a4-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="731a4-131">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="731a4-131">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="731a4-132">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="731a4-132">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="731a4-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="731a4-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="731a4-134">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="731a4-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="731a4-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="731a4-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="731a4-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="731a4-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
