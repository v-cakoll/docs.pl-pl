---
title: '&lt;textMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5e506d48c067871f5921d991c54ad8fb0d1593e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="bc9b8-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="bc9b8-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="bc9b8-103">Określa kodowanie znaków i wiadomości versioning używany dla wiadomości tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="bc9b8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bc9b8-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-105">\<bindings></span></span>  
<span data-ttu-id="bc9b8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-106">\<customBinding></span></span>  
<span data-ttu-id="bc9b8-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-107">\<binding></span></span>  
<span data-ttu-id="bc9b8-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9b8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc9b8-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc9b8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bc9b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc9b8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc9b8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc9b8-112">Attributes</span></span>  
  
|<span data-ttu-id="bc9b8-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bc9b8-113">Attribute</span></span>|<span data-ttu-id="bc9b8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bc9b8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc9b8-115">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="bc9b8-115">maxReadPoolSize</span></span>|<span data-ttu-id="bc9b8-116">Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="bc9b8-117">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="bc9b8-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-118">The default is 64.</span></span>|  
|<span data-ttu-id="bc9b8-119">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="bc9b8-119">maxWritePoolSize</span></span>|<span data-ttu-id="bc9b8-120">Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="bc9b8-121">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="bc9b8-122">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-122">The default is 16.</span></span>|  
|<span data-ttu-id="bc9b8-123">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="bc9b8-123">messageVersion</span></span>|<span data-ttu-id="bc9b8-124">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="bc9b8-125">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="bc9b8-125">Valid values are</span></span><br /><br /> <span data-ttu-id="bc9b8-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="bc9b8-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="bc9b8-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="bc9b8-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="bc9b8-128">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="bc9b8-129">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="bc9b8-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="bc9b8-130">writeEncoding</span></span>|<span data-ttu-id="bc9b8-131">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="bc9b8-132">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="bc9b8-132">Valid values are</span></span><br /><br /> <span data-ttu-id="bc9b8-133">-UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="bc9b8-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="bc9b8-134">-Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="bc9b8-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="bc9b8-135">-Utf8TextEncoding: 8-bitowego kodowania o</span><span class="sxs-lookup"><span data-stu-id="bc9b8-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="bc9b8-136">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="bc9b8-137">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc9b8-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc9b8-138">Child Elements</span></span>  
  
|<span data-ttu-id="bc9b8-139">Element</span><span class="sxs-lookup"><span data-stu-id="bc9b8-139">Element</span></span>|<span data-ttu-id="bc9b8-140">Opis</span><span class="sxs-lookup"><span data-stu-id="bc9b8-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc9b8-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="bc9b8-142">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="bc9b8-143">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc9b8-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc9b8-144">Parent Elements</span></span>  
  
|<span data-ttu-id="bc9b8-145">Element</span><span class="sxs-lookup"><span data-stu-id="bc9b8-145">Element</span></span>|<span data-ttu-id="bc9b8-146">Opis</span><span class="sxs-lookup"><span data-stu-id="bc9b8-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc9b8-147">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bc9b8-148">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9b8-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc9b8-149">Remarks</span></span>  
 <span data-ttu-id="bc9b8-150">Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="bc9b8-151">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-151">Decoding is the reverse process.</span></span> <span data-ttu-id="bc9b8-152">Windows Communication Foundation (WCF) obejmuje trzy rodzaje kodowania protokołu SOAP wiadomości: tekst, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="bc9b8-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="bc9b8-153">Kodowanie tekstu reprezentowany przez `textMessageEncoding` element jest najbardziej współdziałanie, ale najmniej wydajne koder komunikatów XML.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="bc9b8-154">Koder tekstu tworzy wiadomości tekstowych w sieci.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="bc9b8-155">Komunikaty generowane przez ten koder nadają się do usługi WS-* na podstawie interop.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-155">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="bc9b8-156">Klienta usługi sieci Web lub usługi sieci Web zwykle zrozumieć tekstowy XML.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="bc9b8-157">Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania komunikatów XML.</span><span class="sxs-lookup"><span data-stu-id="bc9b8-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9b8-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc9b8-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc9b8-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc9b8-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="bc9b8-160">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="bc9b8-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="bc9b8-161">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="bc9b8-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="bc9b8-162">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bc9b8-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bc9b8-163">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="bc9b8-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bc9b8-164">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="bc9b8-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bc9b8-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bc9b8-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
