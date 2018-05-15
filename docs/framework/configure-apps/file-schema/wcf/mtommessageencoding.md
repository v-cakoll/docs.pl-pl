---
title: '&lt;mtomMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 25990e5583ba1daca378af40e7e56953c95b4a66
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltmtommessageencodinggt"></a><span data-ttu-id="defe4-102">&lt;mtomMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="defe4-102">&lt;mtomMessageEncoding&gt;</span></span>
<span data-ttu-id="defe4-103">Określa kodowanie i wersjonowanie wiadomości używanych dla wiadomości protokołu SOAP wiadomości transmisji optymalizacji mechanizmu (MTOM) na podstawie.</span><span class="sxs-lookup"><span data-stu-id="defe4-103">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="defe4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="defe4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="defe4-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="defe4-105">\<bindings></span></span>  
<span data-ttu-id="defe4-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="defe4-106">\<customBinding></span></span>  
<span data-ttu-id="defe4-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="defe4-107">\<binding></span></span>  
<span data-ttu-id="defe4-108">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="defe4-108">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="defe4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="defe4-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="defe4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="defe4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="defe4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="defe4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="defe4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="defe4-112">Attributes</span></span>  
  
|<span data-ttu-id="defe4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="defe4-113">Attribute</span></span>|<span data-ttu-id="defe4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="defe4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="defe4-115">wartość maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="defe4-115">maxBufferSize</span></span>|<span data-ttu-id="defe4-116">Liczba całkowita określająca maksymalny rozmiar buforu, który może być używany.</span><span class="sxs-lookup"><span data-stu-id="defe4-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="defe4-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="defe4-117">maxReadPoolSize</span></span>|<span data-ttu-id="defe4-118">Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="defe4-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="defe4-119">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="defe4-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="defe4-120">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="defe4-120">The default is 64.</span></span>|  
|<span data-ttu-id="defe4-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="defe4-121">maxWritePoolSize</span></span>|<span data-ttu-id="defe4-122">Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="defe4-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="defe4-123">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="defe4-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="defe4-124">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="defe4-124">The default is 16.</span></span>|  
|<span data-ttu-id="defe4-125">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="defe4-125">messageVersion</span></span>|<span data-ttu-id="defe4-126">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="defe4-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="defe4-127">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="defe4-127">Valid values are</span></span><br /><br /> <span data-ttu-id="defe4-128">-Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="defe4-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="defe4-129">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="defe4-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="defe4-130">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="defe4-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="defe4-131">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="defe4-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="defe4-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="defe4-132">writeEncoding</span></span>|<span data-ttu-id="defe4-133">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="defe4-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="defe4-134">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="defe4-134">Valid values are</span></span><br /><br /> <span data-ttu-id="defe4-135">-UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="defe4-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="defe4-136">-Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="defe4-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="defe4-137">-Utf8TextEncoding: 8-bitowego kodowania o</span><span class="sxs-lookup"><span data-stu-id="defe4-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="defe4-138">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="defe4-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="defe4-139">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="defe4-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="defe4-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="defe4-140">Child Elements</span></span>  
  
|<span data-ttu-id="defe4-141">Element</span><span class="sxs-lookup"><span data-stu-id="defe4-141">Element</span></span>|<span data-ttu-id="defe4-142">Opis</span><span class="sxs-lookup"><span data-stu-id="defe4-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="defe4-143">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="defe4-143">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="defe4-144">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="defe4-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="defe4-145">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="defe4-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="defe4-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="defe4-146">Parent Elements</span></span>  
  
|<span data-ttu-id="defe4-147">Element</span><span class="sxs-lookup"><span data-stu-id="defe4-147">Element</span></span>|<span data-ttu-id="defe4-148">Opis</span><span class="sxs-lookup"><span data-stu-id="defe4-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="defe4-149">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="defe4-149">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="defe4-150">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="defe4-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="defe4-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="defe4-151">Remarks</span></span>  
 <span data-ttu-id="defe4-152">Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="defe4-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="defe4-153">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="defe4-153">Decoding is the reverse process.</span></span> <span data-ttu-id="defe4-154">Windows Communication Foundation (WCF) obejmuje trzy rodzaje kodowania protokołu SOAP wiadomości: tekst, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="defe4-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="defe4-155">`MtomMessageEncoding` Element określa znak kodowanie i wersjonowanie wiadomości i inne ustawienia używane do wiadomości przy użyciu kodowania mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="defe4-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="defe4-156">MTOM jest technologią wydajne przekazywania danych binarnych w wiadomości WCF.</span><span class="sxs-lookup"><span data-stu-id="defe4-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="defe4-157">Koder MTOM podejmuje próbę utworzenia równowagi między wydajności i współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="defe4-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="defe4-158">Kodowanie MTOM przesyła większości XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazując je jako — jest bez użycia konwersji do formatu ich kodowany w standardzie base64.</span><span class="sxs-lookup"><span data-stu-id="defe4-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="defe4-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="defe4-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="defe4-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="defe4-160">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [<span data-ttu-id="defe4-161">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="defe4-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="defe4-162">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="defe4-162">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="defe4-163">Powiązania</span><span class="sxs-lookup"><span data-stu-id="defe4-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="defe4-164">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="defe4-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="defe4-165">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="defe4-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="defe4-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="defe4-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
