---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 70a124fda5bc0e52e1271716f7e2166b7717b49a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933191"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="d12f8-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="d12f8-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="d12f8-102">Określa kodowanie i przechowywanie wersji komunikatów na podstawie komunikatów opartych na mechanizmie optymalizacji transmisji wiadomości (MTOM) protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d12f8-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="d12f8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d12f8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d12f8-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="d12f8-104">\<bindings></span></span>  
<span data-ttu-id="d12f8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d12f8-105">\<customBinding></span></span>  
<span data-ttu-id="d12f8-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d12f8-106">\<binding></span></span>  
<span data-ttu-id="d12f8-107">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="d12f8-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d12f8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d12f8-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d12f8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d12f8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d12f8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d12f8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d12f8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d12f8-111">Attributes</span></span>  
  
|<span data-ttu-id="d12f8-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d12f8-112">Attribute</span></span>|<span data-ttu-id="d12f8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d12f8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d12f8-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="d12f8-114">maxBufferSize</span></span>|<span data-ttu-id="d12f8-115">Liczba całkowita określająca maksymalny rozmiar buforu, który może być używany.</span><span class="sxs-lookup"><span data-stu-id="d12f8-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="d12f8-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d12f8-116">maxReadPoolSize</span></span>|<span data-ttu-id="d12f8-117">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="d12f8-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="d12f8-118">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="d12f8-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d12f8-119">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="d12f8-119">The default is 64.</span></span>|  
|<span data-ttu-id="d12f8-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d12f8-120">maxWritePoolSize</span></span>|<span data-ttu-id="d12f8-121">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="d12f8-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="d12f8-122">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="d12f8-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d12f8-123">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="d12f8-123">The default is 16.</span></span>|  
|<span data-ttu-id="d12f8-124">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="d12f8-124">messageVersion</span></span>|<span data-ttu-id="d12f8-125">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="d12f8-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="d12f8-126">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="d12f8-126">Valid values are</span></span><br /><br /> <span data-ttu-id="d12f8-127">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="d12f8-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="d12f8-128">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="d12f8-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="d12f8-129">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="d12f8-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="d12f8-130">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="d12f8-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="d12f8-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="d12f8-131">writeEncoding</span></span>|<span data-ttu-id="d12f8-132">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="d12f8-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d12f8-133">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="d12f8-133">Valid values are</span></span><br /><br /> <span data-ttu-id="d12f8-134">- UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="d12f8-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="d12f8-135">- Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="d12f8-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="d12f8-136">-   Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="d12f8-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d12f8-137">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="d12f8-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="d12f8-138">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="d12f8-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d12f8-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d12f8-139">Child Elements</span></span>  
  
|<span data-ttu-id="d12f8-140">Element</span><span class="sxs-lookup"><span data-stu-id="d12f8-140">Element</span></span>|<span data-ttu-id="d12f8-141">Opis</span><span class="sxs-lookup"><span data-stu-id="d12f8-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d12f8-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d12f8-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="d12f8-143">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d12f8-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d12f8-144">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="d12f8-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d12f8-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d12f8-145">Parent Elements</span></span>  
  
|<span data-ttu-id="d12f8-146">Element</span><span class="sxs-lookup"><span data-stu-id="d12f8-146">Element</span></span>|<span data-ttu-id="d12f8-147">Opis</span><span class="sxs-lookup"><span data-stu-id="d12f8-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d12f8-148">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="d12f8-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="d12f8-149">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d12f8-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d12f8-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d12f8-150">Remarks</span></span>  
 <span data-ttu-id="d12f8-151">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="d12f8-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="d12f8-152">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="d12f8-152">Decoding is the reverse process.</span></span> <span data-ttu-id="d12f8-153">Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla komunikatów SOAP: Mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="d12f8-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="d12f8-154">`MtomMessageEncoding` Element określa kodowanie znaków i przechowywanie wersji komunikatów oraz inne ustawienia używane w przypadku komunikatów przy użyciu kodowania mechanizmu optymalizacji transmisji komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="d12f8-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="d12f8-155">MTOM to wydajna technologia przesyłania danych binarnych w komunikatach programu WCF.</span><span class="sxs-lookup"><span data-stu-id="d12f8-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="d12f8-156">Koder MTOM próbuje utworzyć balans między wydajnością i współdziałaniem.</span><span class="sxs-lookup"><span data-stu-id="d12f8-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="d12f8-157">Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich jako-is, bez konwersji do formatu zakodowanego algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="d12f8-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d12f8-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="d12f8-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d12f8-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d12f8-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="d12f8-160">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="d12f8-160">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="d12f8-161">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="d12f8-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="d12f8-162">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d12f8-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d12f8-163">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="d12f8-163">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d12f8-164">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d12f8-164">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d12f8-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d12f8-165">\<customBinding></span></span>](custombinding.md)
