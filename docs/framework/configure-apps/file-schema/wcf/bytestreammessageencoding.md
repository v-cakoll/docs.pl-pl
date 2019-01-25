---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 92ae3dc10e0ae734a3113e22f175f4d010ca55b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541862"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="1f2ee-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="1f2ee-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="1f2ee-103">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="1f2ee-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1f2ee-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1f2ee-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1f2ee-105">\<bindings></span></span>  
<span data-ttu-id="1f2ee-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1f2ee-106">\<customBinding></span></span>  
<span data-ttu-id="1f2ee-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1f2ee-107">\<binding></span></span>  
<span data-ttu-id="1f2ee-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="1f2ee-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f2ee-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f2ee-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f2ee-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f2ee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1f2ee-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f2ee-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f2ee-112">Attributes</span></span>  
  
|<span data-ttu-id="1f2ee-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1f2ee-113">Attribute</span></span>|<span data-ttu-id="1f2ee-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2ee-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f2ee-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="1f2ee-115">messageVersion</span></span>|<span data-ttu-id="1f2ee-116">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="1f2ee-117">Tę właściwość można ustawić tylko wartość wersji wiadomości <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="1f2ee-118">Koder komunikatów strumień bajtów nie obsługuje inne wersje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="1f2ee-119">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f2ee-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f2ee-120">Child Elements</span></span>  
  
|<span data-ttu-id="1f2ee-121">Element</span><span class="sxs-lookup"><span data-stu-id="1f2ee-121">Element</span></span>|<span data-ttu-id="1f2ee-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2ee-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f2ee-123">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="1f2ee-123">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="1f2ee-124">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1f2ee-125">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f2ee-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f2ee-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1f2ee-127">Element</span><span class="sxs-lookup"><span data-stu-id="1f2ee-127">Element</span></span>|<span data-ttu-id="1f2ee-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2ee-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f2ee-129">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1f2ee-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1f2ee-130">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1f2ee-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f2ee-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f2ee-131">See also</span></span>
- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="1f2ee-132">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="1f2ee-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="1f2ee-133">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="1f2ee-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="1f2ee-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1f2ee-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1f2ee-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1f2ee-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1f2ee-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1f2ee-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1f2ee-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1f2ee-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
