---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1788300407ad84a5ff7e3929eaa728f5399961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="1be72-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="1be72-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="1be72-103">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="1be72-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="1be72-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1be72-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1be72-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1be72-105">\<bindings></span></span>  
<span data-ttu-id="1be72-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1be72-106">\<customBinding></span></span>  
<span data-ttu-id="1be72-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1be72-107">\<binding></span></span>  
<span data-ttu-id="1be72-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="1be72-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be72-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1be72-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1be72-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1be72-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1be72-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1be72-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1be72-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1be72-112">Attributes</span></span>  
  
|<span data-ttu-id="1be72-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1be72-113">Attribute</span></span>|<span data-ttu-id="1be72-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1be72-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1be72-115">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="1be72-115">messageVersion</span></span>|<span data-ttu-id="1be72-116">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1be72-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="1be72-117">Tej właściwości można ustawić tylko wartość wersji komunikatu <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="1be72-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="1be72-118">Koder komunikatów strumień bajtów nie obsługuje inne wersje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1be72-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="1be72-119">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="1be72-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1be72-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1be72-120">Child Elements</span></span>  
  
|<span data-ttu-id="1be72-121">Element</span><span class="sxs-lookup"><span data-stu-id="1be72-121">Element</span></span>|<span data-ttu-id="1be72-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1be72-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1be72-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="1be72-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="1be72-124">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="1be72-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1be72-125">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1be72-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1be72-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1be72-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1be72-127">Element</span><span class="sxs-lookup"><span data-stu-id="1be72-127">Element</span></span>|<span data-ttu-id="1be72-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1be72-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1be72-129">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1be72-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1be72-130">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1be72-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1be72-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1be72-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="1be72-132">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="1be72-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="1be72-133">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="1be72-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="1be72-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1be72-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1be72-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="1be72-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1be72-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="1be72-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1be72-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1be72-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
