---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736219"
---
# <a name="textmessageencoding"></a><span data-ttu-id="480b7-101">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="480b7-101">\<textMessageEncoding></span></span>
<span data-ttu-id="480b7-102">Określa kodowanie znaków i przechowywanie wersji komunikatów używanych w przypadku tekstowych wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="480b7-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="480b7-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="480b7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="480b7-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="480b7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="480b7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="480b7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="480b7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="480b7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="480b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="480b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="480b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="480b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="480b7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="480b7-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="480b7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="480b7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="480b7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="480b7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="480b7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="480b7-112">Attributes</span></span>  
  
|<span data-ttu-id="480b7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="480b7-113">Attribute</span></span>|<span data-ttu-id="480b7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="480b7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="480b7-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="480b7-115">maxReadPoolSize</span></span>|<span data-ttu-id="480b7-116">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="480b7-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="480b7-117">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="480b7-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="480b7-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="480b7-118">The default is 64.</span></span>|  
|<span data-ttu-id="480b7-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="480b7-119">maxWritePoolSize</span></span>|<span data-ttu-id="480b7-120">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="480b7-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="480b7-121">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="480b7-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="480b7-122">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="480b7-122">The default is 16.</span></span>|  
|<span data-ttu-id="480b7-123">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="480b7-123">messageVersion</span></span>|<span data-ttu-id="480b7-124">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="480b7-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="480b7-125">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="480b7-125">Valid values are</span></span><br /><br /> <span data-ttu-id="480b7-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="480b7-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="480b7-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="480b7-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="480b7-128">- Soap11</span><span class="sxs-lookup"><span data-stu-id="480b7-128">-   Soap11</span></span><br /><span data-ttu-id="480b7-129">- Soap12</span><span class="sxs-lookup"><span data-stu-id="480b7-129">-  Soap12</span></span><br /><br /><span data-ttu-id="480b7-130">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="480b7-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="480b7-131">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="480b7-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="480b7-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="480b7-132">writeEncoding</span></span>|<span data-ttu-id="480b7-133">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="480b7-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="480b7-134">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="480b7-134">Valid values are</span></span><br /><br /> <span data-ttu-id="480b7-135">-UnicodeFffeTextEncoding: kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="480b7-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="480b7-136">-Utf16TextEncoding: kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="480b7-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="480b7-137">-Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="480b7-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="480b7-138">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="480b7-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="480b7-139">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="480b7-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="480b7-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="480b7-140">Child Elements</span></span>  
  
|<span data-ttu-id="480b7-141">Element</span><span class="sxs-lookup"><span data-stu-id="480b7-141">Element</span></span>|<span data-ttu-id="480b7-142">Opis</span><span class="sxs-lookup"><span data-stu-id="480b7-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="480b7-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="480b7-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="480b7-144">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="480b7-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="480b7-145">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="480b7-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="480b7-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="480b7-146">Parent Elements</span></span>  
  
|<span data-ttu-id="480b7-147">Element</span><span class="sxs-lookup"><span data-stu-id="480b7-147">Element</span></span>|<span data-ttu-id="480b7-148">Opis</span><span class="sxs-lookup"><span data-stu-id="480b7-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="480b7-149">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="480b7-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="480b7-150">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="480b7-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="480b7-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="480b7-151">Remarks</span></span>  
 <span data-ttu-id="480b7-152">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="480b7-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="480b7-153">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="480b7-153">Decoding is the reverse process.</span></span> <span data-ttu-id="480b7-154">Windows Communication Foundation (WCF) zawiera trzy typy kodowania komunikatów protokołu SOAP: tekst, binarny i mechanizm optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="480b7-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="480b7-155">Kodowanie tekstu reprezentowane przez element `textMessageEncoding` jest najbardziej interoperacyjny, ale najmniej wydajny koder dla wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="480b7-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="480b7-156">Koder tekstowy tworzy wiadomości tekstowe w sieci.</span><span class="sxs-lookup"><span data-stu-id="480b7-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="480b7-157">Komunikaty generowane przez ten koder są odpowiednie dla międzyoperacyjności opartego na protokole WS-\*.</span><span class="sxs-lookup"><span data-stu-id="480b7-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="480b7-158">Usługa sieci Web lub klient usługi sieci Web może ogólnie zrozumieć tekst XML.</span><span class="sxs-lookup"><span data-stu-id="480b7-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="480b7-159">Jednak przesyłanie dużych bloków danych binarnych jako tekstu jest najmniejszą efektywną metodą kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="480b7-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="480b7-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="480b7-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="480b7-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="480b7-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="480b7-162">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="480b7-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="480b7-163">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="480b7-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="480b7-164">Powiązania</span><span class="sxs-lookup"><span data-stu-id="480b7-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="480b7-165">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="480b7-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="480b7-166">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="480b7-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="480b7-167">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="480b7-167">\<customBinding></span></span>](custombinding.md)
