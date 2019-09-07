---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 1494cee0e412bebc6637ad73354f7c91dc636e15
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399434"
---
# <a name="textmessageencoding"></a><span data-ttu-id="62211-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="62211-101">\<textMessageEncoding></span></span>
<span data-ttu-id="62211-102">Określa kodowanie znaków i przechowywanie wersji komunikatów używanych w przypadku tekstowych wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="62211-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="62211-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62211-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62211-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62211-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62211-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="62211-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="62211-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="62211-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="62211-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="62211-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="62211-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="62211-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62211-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="62211-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62211-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62211-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62211-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62211-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62211-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62211-112">Attributes</span></span>  
  
|<span data-ttu-id="62211-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62211-113">Attribute</span></span>|<span data-ttu-id="62211-114">Opis</span><span class="sxs-lookup"><span data-stu-id="62211-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62211-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="62211-115">maxReadPoolSize</span></span>|<span data-ttu-id="62211-116">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="62211-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="62211-117">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="62211-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="62211-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="62211-118">The default is 64.</span></span>|  
|<span data-ttu-id="62211-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="62211-119">maxWritePoolSize</span></span>|<span data-ttu-id="62211-120">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="62211-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="62211-121">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="62211-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="62211-122">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="62211-122">The default is 16.</span></span>|  
|<span data-ttu-id="62211-123">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="62211-123">messageVersion</span></span>|<span data-ttu-id="62211-124">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="62211-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="62211-125">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="62211-125">Valid values are</span></span><br /><br /> <span data-ttu-id="62211-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="62211-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="62211-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="62211-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="62211-128">- Soap11</span><span class="sxs-lookup"><span data-stu-id="62211-128">-   Soap11</span></span><br /><span data-ttu-id="62211-129">- Soap12</span><span class="sxs-lookup"><span data-stu-id="62211-129">-  Soap12</span></span><br /><br /><span data-ttu-id="62211-130">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="62211-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="62211-131">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="62211-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="62211-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="62211-132">writeEncoding</span></span>|<span data-ttu-id="62211-133">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="62211-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="62211-134">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="62211-134">Valid values are</span></span><br /><br /> <span data-ttu-id="62211-135">- UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="62211-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="62211-136">- Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="62211-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="62211-137">-   Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="62211-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="62211-138">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="62211-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="62211-139">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="62211-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62211-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62211-140">Child Elements</span></span>  
  
|<span data-ttu-id="62211-141">Element</span><span class="sxs-lookup"><span data-stu-id="62211-141">Element</span></span>|<span data-ttu-id="62211-142">Opis</span><span class="sxs-lookup"><span data-stu-id="62211-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62211-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62211-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="62211-144">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="62211-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="62211-145">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="62211-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62211-146">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62211-146">Parent Elements</span></span>  
  
|<span data-ttu-id="62211-147">Element</span><span class="sxs-lookup"><span data-stu-id="62211-147">Element</span></span>|<span data-ttu-id="62211-148">Opis</span><span class="sxs-lookup"><span data-stu-id="62211-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62211-149">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="62211-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="62211-150">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="62211-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62211-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62211-151">Remarks</span></span>  
 <span data-ttu-id="62211-152">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="62211-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="62211-153">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="62211-153">Decoding is the reverse process.</span></span> <span data-ttu-id="62211-154">Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla komunikatów SOAP: Mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="62211-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="62211-155">Kodowanie tekstu reprezentowane przez `textMessageEncoding` element to najbardziej interoperacyjny, ale najmniej wydajny koder dla wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="62211-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="62211-156">Koder tekstowy tworzy wiadomości tekstowe w sieci.</span><span class="sxs-lookup"><span data-stu-id="62211-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="62211-157">Komunikaty generowane przez ten koder są odpowiednie dla międzyoperacyjności opartego na protokole WS-\*.</span><span class="sxs-lookup"><span data-stu-id="62211-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="62211-158">Usługa sieci Web lub klient usługi sieci Web może ogólnie zrozumieć tekst XML.</span><span class="sxs-lookup"><span data-stu-id="62211-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="62211-159">Jednak przesyłanie dużych bloków danych binarnych jako tekstu jest najmniejszą efektywną metodą kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="62211-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62211-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="62211-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="62211-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62211-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="62211-162">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="62211-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="62211-163">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="62211-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="62211-164">Powiązania</span><span class="sxs-lookup"><span data-stu-id="62211-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="62211-165">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="62211-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="62211-166">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="62211-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="62211-167">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="62211-167">\<customBinding></span></span>](custombinding.md)
