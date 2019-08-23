---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e2fec2c2e5979b08ed0d832f636b3d0847b9a5dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915659"
---
# <a name="textmessageencoding"></a><span data-ttu-id="6db7f-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="6db7f-101">\<textMessageEncoding></span></span>
<span data-ttu-id="6db7f-102">Określa kodowanie znaków i przechowywanie wersji komunikatów używanych w przypadku tekstowych wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="6db7f-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="6db7f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6db7f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6db7f-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="6db7f-104">\<bindings></span></span>  
<span data-ttu-id="6db7f-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6db7f-105">\<customBinding></span></span>  
<span data-ttu-id="6db7f-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="6db7f-106">\<binding></span></span>  
<span data-ttu-id="6db7f-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="6db7f-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db7f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6db7f-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6db7f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6db7f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6db7f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6db7f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6db7f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6db7f-111">Attributes</span></span>  
  
|<span data-ttu-id="6db7f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6db7f-112">Attribute</span></span>|<span data-ttu-id="6db7f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6db7f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6db7f-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="6db7f-114">maxReadPoolSize</span></span>|<span data-ttu-id="6db7f-115">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="6db7f-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="6db7f-116">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="6db7f-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="6db7f-117">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="6db7f-117">The default is 64.</span></span>|  
|<span data-ttu-id="6db7f-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="6db7f-118">maxWritePoolSize</span></span>|<span data-ttu-id="6db7f-119">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="6db7f-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="6db7f-120">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="6db7f-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="6db7f-121">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="6db7f-121">The default is 16.</span></span>|  
|<span data-ttu-id="6db7f-122">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="6db7f-122">messageVersion</span></span>|<span data-ttu-id="6db7f-123">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="6db7f-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="6db7f-124">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="6db7f-124">Valid values are</span></span><br /><br /> <span data-ttu-id="6db7f-125">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="6db7f-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="6db7f-126">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="6db7f-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="6db7f-127">- Soap11</span><span class="sxs-lookup"><span data-stu-id="6db7f-127">-   Soap11</span></span><br /><span data-ttu-id="6db7f-128">- Soap12</span><span class="sxs-lookup"><span data-stu-id="6db7f-128">-  Soap12</span></span><br /><br /><span data-ttu-id="6db7f-129">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="6db7f-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="6db7f-130">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="6db7f-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="6db7f-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="6db7f-131">writeEncoding</span></span>|<span data-ttu-id="6db7f-132">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="6db7f-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="6db7f-133">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="6db7f-133">Valid values are</span></span><br /><br /> <span data-ttu-id="6db7f-134">- UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="6db7f-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="6db7f-135">- Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="6db7f-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="6db7f-136">-   Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="6db7f-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="6db7f-137">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="6db7f-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="6db7f-138">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6db7f-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6db7f-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6db7f-139">Child Elements</span></span>  
  
|<span data-ttu-id="6db7f-140">Element</span><span class="sxs-lookup"><span data-stu-id="6db7f-140">Element</span></span>|<span data-ttu-id="6db7f-141">Opis</span><span class="sxs-lookup"><span data-stu-id="6db7f-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6db7f-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6db7f-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="6db7f-143">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6db7f-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6db7f-144">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="6db7f-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6db7f-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6db7f-145">Parent Elements</span></span>  
  
|<span data-ttu-id="6db7f-146">Element</span><span class="sxs-lookup"><span data-stu-id="6db7f-146">Element</span></span>|<span data-ttu-id="6db7f-147">Opis</span><span class="sxs-lookup"><span data-stu-id="6db7f-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6db7f-148">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="6db7f-148">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="6db7f-149">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6db7f-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6db7f-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6db7f-150">Remarks</span></span>  
 <span data-ttu-id="6db7f-151">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="6db7f-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="6db7f-152">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="6db7f-152">Decoding is the reverse process.</span></span> <span data-ttu-id="6db7f-153">Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla komunikatów SOAP: Mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="6db7f-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="6db7f-154">Kodowanie tekstu reprezentowane przez `textMessageEncoding` element to najbardziej interoperacyjny, ale najmniej wydajny koder dla wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="6db7f-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="6db7f-155">Koder tekstowy tworzy wiadomości tekstowe w sieci.</span><span class="sxs-lookup"><span data-stu-id="6db7f-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="6db7f-156">Komunikaty generowane przez ten koder są odpowiednie dla międzyoperacyjności opartego na protokole WS-\*.</span><span class="sxs-lookup"><span data-stu-id="6db7f-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="6db7f-157">Usługa sieci Web lub klient usługi sieci Web może ogólnie zrozumieć tekst XML.</span><span class="sxs-lookup"><span data-stu-id="6db7f-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="6db7f-158">Jednak przesyłanie dużych bloków danych binarnych jako tekstu jest najmniejszą efektywną metodą kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="6db7f-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db7f-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="6db7f-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="6db7f-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6db7f-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="6db7f-161">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="6db7f-161">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="6db7f-162">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="6db7f-162">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="6db7f-163">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6db7f-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6db7f-164">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="6db7f-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6db7f-165">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6db7f-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6db7f-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6db7f-166">\<customBinding></span></span>](custombinding.md)
