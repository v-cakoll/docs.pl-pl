---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 9d38f16cdeb8b769f4026ccb29f9129e93ef031c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146462"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="f072e-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="f072e-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="f072e-103">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="f072e-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="f072e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f072e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f072e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f072e-105">\<bindings></span></span>  
<span data-ttu-id="f072e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f072e-106">\<customBinding></span></span>  
<span data-ttu-id="f072e-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f072e-107">\<binding></span></span>  
<span data-ttu-id="f072e-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="f072e-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f072e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f072e-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f072e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f072e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f072e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f072e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f072e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f072e-112">Attributes</span></span>  
  
|<span data-ttu-id="f072e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f072e-113">Attribute</span></span>|<span data-ttu-id="f072e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f072e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f072e-115">Element messageVersion</span><span class="sxs-lookup"><span data-stu-id="f072e-115">messageVersion</span></span>|<span data-ttu-id="f072e-116">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f072e-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="f072e-117">Tę właściwość można ustawić tylko wartość wersji wiadomości <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="f072e-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="f072e-118">Koder komunikatów strumień bajtów nie obsługuje inne wersje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f072e-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="f072e-119">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="f072e-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f072e-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f072e-120">Child Elements</span></span>  
  
|<span data-ttu-id="f072e-121">Element</span><span class="sxs-lookup"><span data-stu-id="f072e-121">Element</span></span>|<span data-ttu-id="f072e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f072e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f072e-123">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="f072e-123">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f072e-124">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="f072e-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f072e-125">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f072e-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f072e-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f072e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f072e-127">Element</span><span class="sxs-lookup"><span data-stu-id="f072e-127">Element</span></span>|<span data-ttu-id="f072e-128">Opis</span><span class="sxs-lookup"><span data-stu-id="f072e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f072e-129">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f072e-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f072e-130">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f072e-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f072e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f072e-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="f072e-132">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="f072e-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="f072e-133">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="f072e-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="f072e-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f072e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f072e-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f072e-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f072e-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f072e-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f072e-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f072e-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
