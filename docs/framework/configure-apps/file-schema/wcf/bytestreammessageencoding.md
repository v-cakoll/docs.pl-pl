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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 165bf4cd1c0c5c1a6adae91650d38984bc47ef6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="5d845-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="5d845-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="5d845-103">Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="5d845-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="5d845-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5d845-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5d845-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5d845-105">\<bindings></span></span>  
<span data-ttu-id="5d845-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5d845-106">\<customBinding></span></span>  
<span data-ttu-id="5d845-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5d845-107">\<binding></span></span>  
<span data-ttu-id="5d845-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="5d845-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d845-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d845-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d845-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d845-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5d845-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d845-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d845-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d845-112">Attributes</span></span>  
  
|<span data-ttu-id="5d845-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5d845-113">Attribute</span></span>|<span data-ttu-id="5d845-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5d845-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d845-115">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="5d845-115">messageVersion</span></span>|<span data-ttu-id="5d845-116">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5d845-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="5d845-117">Tej właściwości można ustawić tylko wartość wersji komunikatu <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d845-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="5d845-118">Koder komunikatów strumień bajtów nie obsługuje inne wersje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5d845-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="5d845-119">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="5d845-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d845-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d845-120">Child Elements</span></span>  
  
|<span data-ttu-id="5d845-121">Element</span><span class="sxs-lookup"><span data-stu-id="5d845-121">Element</span></span>|<span data-ttu-id="5d845-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5d845-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d845-123">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="5d845-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="5d845-124">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="5d845-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5d845-125">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5d845-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d845-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d845-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5d845-127">Element</span><span class="sxs-lookup"><span data-stu-id="5d845-127">Element</span></span>|<span data-ttu-id="5d845-128">Opis</span><span class="sxs-lookup"><span data-stu-id="5d845-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d845-129">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5d845-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5d845-130">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5d845-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d845-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d845-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="5d845-132">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="5d845-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="5d845-133">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="5d845-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="5d845-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5d845-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5d845-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="5d845-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5d845-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="5d845-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5d845-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5d845-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
