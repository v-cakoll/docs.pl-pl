---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e6e6d1907d89a09a72594a836f2192e9ad9c4290
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614119"
---
# <a name="textmessageencoding"></a><span data-ttu-id="b4978-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="b4978-101">\<textMessageEncoding></span></span>
<span data-ttu-id="b4978-102">Określa kodowanie znaków i wiadomości versioning używany dla wiadomości tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="b4978-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="b4978-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b4978-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b4978-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b4978-104">\<bindings></span></span>  
<span data-ttu-id="b4978-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b4978-105">\<customBinding></span></span>  
<span data-ttu-id="b4978-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b4978-106">\<binding></span></span>  
<span data-ttu-id="b4978-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="b4978-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4978-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4978-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4978-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b4978-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b4978-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b4978-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4978-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b4978-111">Attributes</span></span>  
  
|<span data-ttu-id="b4978-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b4978-112">Attribute</span></span>|<span data-ttu-id="b4978-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b4978-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b4978-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b4978-114">maxReadPoolSize</span></span>|<span data-ttu-id="b4978-115">Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="b4978-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="b4978-116">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="b4978-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b4978-117">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="b4978-117">The default is 64.</span></span>|  
|<span data-ttu-id="b4978-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b4978-118">maxWritePoolSize</span></span>|<span data-ttu-id="b4978-119">Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="b4978-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="b4978-120">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="b4978-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b4978-121">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="b4978-121">The default is 16.</span></span>|  
|<span data-ttu-id="b4978-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="b4978-122">messageVersion</span></span>|<span data-ttu-id="b4978-123">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b4978-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="b4978-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="b4978-124">Valid values are</span></span><br /><br /> <span data-ttu-id="b4978-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="b4978-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="b4978-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="b4978-126">-   Soap12Addressing10</span></span><br /><span data-ttu-id="b4978-127">-Soap11</span><span class="sxs-lookup"><span data-stu-id="b4978-127">-   Soap11</span></span><br /><span data-ttu-id="b4978-128">-Soap12</span><span class="sxs-lookup"><span data-stu-id="b4978-128">-  Soap12</span></span><br /><br /><span data-ttu-id="b4978-129">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="b4978-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="b4978-130">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="b4978-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="b4978-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="b4978-131">writeEncoding</span></span>|<span data-ttu-id="b4978-132">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="b4978-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b4978-133">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="b4978-133">Valid values are</span></span><br /><br /> <span data-ttu-id="b4978-134">-   UnicodeFffeTextEncoding: Unicode BigEndian z kodowaniem</span><span class="sxs-lookup"><span data-stu-id="b4978-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="b4978-135">-   Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="b4978-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="b4978-136">-   Utf8TextEncoding: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="b4978-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b4978-137">The default is Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="b4978-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="b4978-138">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b4978-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4978-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b4978-139">Child Elements</span></span>  
  
|<span data-ttu-id="b4978-140">Element</span><span class="sxs-lookup"><span data-stu-id="b4978-140">Element</span></span>|<span data-ttu-id="b4978-141">Opis</span><span class="sxs-lookup"><span data-stu-id="b4978-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4978-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b4978-142">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b4978-143">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="b4978-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b4978-144">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b4978-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4978-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b4978-145">Parent Elements</span></span>  
  
|<span data-ttu-id="b4978-146">Element</span><span class="sxs-lookup"><span data-stu-id="b4978-146">Element</span></span>|<span data-ttu-id="b4978-147">Opis</span><span class="sxs-lookup"><span data-stu-id="b4978-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4978-148">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b4978-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b4978-149">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b4978-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4978-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4978-150">Remarks</span></span>  
 <span data-ttu-id="b4978-151">Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="b4978-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="b4978-152">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="b4978-152">Decoding is the reverse process.</span></span> <span data-ttu-id="b4978-153">Windows Communication Foundation (WCF) obejmuje trzy typy kodowania dla protokołu SOAP wiadomości: Tekst pliku binarnego i mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b4978-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b4978-154">Kodowanie tekstu reprezentowany przez `textMessageEncoding` element jest najbardziej elementy mogły współdziałać, ale co najmniej wydajne kodera komunikatów XML.</span><span class="sxs-lookup"><span data-stu-id="b4978-154">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="b4978-155">Koder tekstu tworzy oparte na tekście wiadomości na łączu.</span><span class="sxs-lookup"><span data-stu-id="b4978-155">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="b4978-156">Komunikaty generowane przez ten koder nadają się dla protokołu WS-\* na podstawie międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="b4978-156">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="b4978-157">Klient usługi sieci Web lub usługa sieci Web zazwyczaj może zrozumieć tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="b4978-157">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="b4978-158">Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="b4978-158">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4978-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4978-159">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b4978-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4978-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="b4978-161">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="b4978-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="b4978-162">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="b4978-162">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="b4978-163">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b4978-163">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b4978-164">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b4978-164">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b4978-165">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b4978-165">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b4978-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b4978-166">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
