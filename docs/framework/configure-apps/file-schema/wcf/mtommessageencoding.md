---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738837"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="39825-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="39825-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="39825-102">Określa kodowanie i przechowywanie wersji komunikatów na podstawie komunikatów opartych na mechanizmie optymalizacji transmisji wiadomości (MTOM) protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="39825-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="39825-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="39825-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39825-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="39825-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="39825-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="39825-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="39825-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="39825-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="39825-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="39825-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="39825-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="39825-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39825-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="39825-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39825-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39825-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39825-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39825-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39825-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39825-112">Attributes</span></span>  
  
|<span data-ttu-id="39825-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39825-113">Attribute</span></span>|<span data-ttu-id="39825-114">Opis</span><span class="sxs-lookup"><span data-stu-id="39825-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39825-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="39825-115">maxBufferSize</span></span>|<span data-ttu-id="39825-116">Liczba całkowita określająca maksymalny rozmiar buforu, który może być używany.</span><span class="sxs-lookup"><span data-stu-id="39825-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="39825-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="39825-117">maxReadPoolSize</span></span>|<span data-ttu-id="39825-118">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="39825-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="39825-119">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="39825-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="39825-120">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="39825-120">The default is 64.</span></span>|  
|<span data-ttu-id="39825-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="39825-121">maxWritePoolSize</span></span>|<span data-ttu-id="39825-122">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="39825-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="39825-123">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="39825-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="39825-124">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="39825-124">The default is 16.</span></span>|  
|<span data-ttu-id="39825-125">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="39825-125">messageVersion</span></span>|<span data-ttu-id="39825-126">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="39825-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="39825-127">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="39825-127">Valid values are</span></span><br /><br /> <span data-ttu-id="39825-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="39825-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="39825-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="39825-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="39825-130">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="39825-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="39825-131">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="39825-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="39825-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="39825-132">writeEncoding</span></span>|<span data-ttu-id="39825-133">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="39825-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="39825-134">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="39825-134">Valid values are</span></span><br /><br /> <span data-ttu-id="39825-135">-UnicodeFffeTextEncoding: kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="39825-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="39825-136">-Utf16TextEncoding: kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="39825-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="39825-137">-Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="39825-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="39825-138">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="39825-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="39825-139">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="39825-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39825-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39825-140">Child Elements</span></span>  
  
|<span data-ttu-id="39825-141">Element</span><span class="sxs-lookup"><span data-stu-id="39825-141">Element</span></span>|<span data-ttu-id="39825-142">Opis</span><span class="sxs-lookup"><span data-stu-id="39825-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39825-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="39825-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="39825-144">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="39825-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="39825-145">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="39825-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39825-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39825-146">Parent Elements</span></span>  
  
|<span data-ttu-id="39825-147">Element</span><span class="sxs-lookup"><span data-stu-id="39825-147">Element</span></span>|<span data-ttu-id="39825-148">Opis</span><span class="sxs-lookup"><span data-stu-id="39825-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39825-149">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="39825-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="39825-150">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="39825-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39825-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39825-151">Remarks</span></span>  
 <span data-ttu-id="39825-152">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="39825-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="39825-153">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="39825-153">Decoding is the reverse process.</span></span> <span data-ttu-id="39825-154">Windows Communication Foundation (WCF) zawiera trzy typy kodowania komunikatów protokołu SOAP: tekst, binarny i mechanizm optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="39825-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="39825-155">`MtomMessageEncoding` element określa kodowanie znaków i przechowywanie wersji komunikatów oraz inne ustawienia używane w przypadku komunikatów przy użyciu kodowania mechanizmu optymalizacji transmisji komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="39825-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="39825-156">MTOM to wydajna technologia przesyłania danych binarnych w komunikatach programu WCF.</span><span class="sxs-lookup"><span data-stu-id="39825-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="39825-157">Koder MTOM próbuje utworzyć balans między wydajnością i współdziałaniem.</span><span class="sxs-lookup"><span data-stu-id="39825-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="39825-158">Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich jako-is, bez konwersji do formatu zakodowanego algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="39825-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39825-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="39825-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="39825-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39825-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="39825-161">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="39825-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="39825-162">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="39825-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="39825-163">Powiązania</span><span class="sxs-lookup"><span data-stu-id="39825-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="39825-164">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="39825-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="39825-165">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="39825-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="39825-166">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="39825-166">\<customBinding></span></span>](custombinding.md)
