---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 503c0edf3a21b3fb0f57b5199aa2a1a17df4222d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="7c712-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="7c712-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="7c712-103">Definiuje binarnego kodera wiadomości, który koduje wiadomości Windows Communication Foundation (WCF) w dane binarne w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="7c712-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="7c712-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7c712-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7c712-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7c712-105">\<bindings></span></span>  
<span data-ttu-id="7c712-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7c712-106">\<customBinding></span></span>  
<span data-ttu-id="7c712-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7c712-107">\<binding></span></span>  
<span data-ttu-id="7c712-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="7c712-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c712-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c712-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c712-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c712-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c712-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c712-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c712-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c712-112">Attributes</span></span>  
  
|<span data-ttu-id="7c712-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7c712-113">Attribute</span></span>|<span data-ttu-id="7c712-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7c712-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c712-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="7c712-115">maxReadPoolSize</span></span>|<span data-ttu-id="7c712-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="7c712-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="7c712-117">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="7c712-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="7c712-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="7c712-118">The default is 64.</span></span>|  
|<span data-ttu-id="7c712-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="7c712-119">maxSessionSize</span></span>|<span data-ttu-id="7c712-120">Dodatnia liczba całkowita, która ustawia rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="7c712-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="7c712-121">Większy bufor zwiększa kodowania szybkość kosztem rozmiar zestawu roboczego.</span><span class="sxs-lookup"><span data-stu-id="7c712-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="7c712-122">Wartość domyślna to 2048.</span><span class="sxs-lookup"><span data-stu-id="7c712-122">The default is 2048.</span></span>|  
|<span data-ttu-id="7c712-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="7c712-123">maxWritePoolSize</span></span>|<span data-ttu-id="7c712-124">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="7c712-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="7c712-125">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="7c712-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="7c712-126">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="7c712-126">The default is 16.</span></span>|  
|<span data-ttu-id="7c712-127">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="7c712-127">messageVersion</span></span>|<span data-ttu-id="7c712-128">Określa komunikatu protokołu SOAP i wersji WS-Addressing, które są używane lub oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="7c712-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c712-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c712-129">Child Elements</span></span>  
  
|<span data-ttu-id="7c712-130">Element</span><span class="sxs-lookup"><span data-stu-id="7c712-130">Element</span></span>|<span data-ttu-id="7c712-131">Opis</span><span class="sxs-lookup"><span data-stu-id="7c712-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c712-132">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="7c712-132">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7c712-133">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="7c712-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7c712-134">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7c712-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c712-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c712-135">Parent Elements</span></span>  
  
|<span data-ttu-id="7c712-136">Element</span><span class="sxs-lookup"><span data-stu-id="7c712-136">Element</span></span>|<span data-ttu-id="7c712-137">Opis</span><span class="sxs-lookup"><span data-stu-id="7c712-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c712-138">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7c712-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7c712-139">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7c712-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c712-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c712-140">Remarks</span></span>  
 <span data-ttu-id="7c712-141">Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="7c712-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="7c712-142">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="7c712-142">Decoding is the reverse process.</span></span> <span data-ttu-id="7c712-143">Windows Communication Foundation (WCF) obejmuje trzy rodzaje kodowania protokołu SOAP wiadomości: tekst, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="7c712-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="7c712-144">`binaryMessageEncoding` Element określa Format binarny .NET dla formatu XML i opcji, aby określić kodowania znaków i wersji protokołu SOAP i WS-Addressing do użycia.</span><span class="sxs-lookup"><span data-stu-id="7c712-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="7c712-145">Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w dane binarne w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="7c712-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="7c712-146">Chociaż ten typ kodowania w wyniku bardzo szybko transmisję wiadomości, współdziałanie opartych na WS-\* standardów zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="7c712-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c712-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c712-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c712-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c712-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="7c712-149">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="7c712-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="7c712-150">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="7c712-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="7c712-151">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7c712-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7c712-152">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="7c712-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7c712-153">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7c712-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7c712-154">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7c712-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
