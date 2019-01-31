---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: c9f8347b4ee5f8fdbcf5c65c9a38b171ea6309de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289604"
---
# <a name="textmessageencoding"></a><span data-ttu-id="9bca5-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="9bca5-101">\<textMessageEncoding></span></span>
<span data-ttu-id="9bca5-102">Określa kodowanie znaków i wiadomości versioning używany dla wiadomości tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="9bca5-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="9bca5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9bca5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="9bca5-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9bca5-104">\<bindings></span></span>  
<span data-ttu-id="9bca5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9bca5-105">\<customBinding></span></span>  
<span data-ttu-id="9bca5-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9bca5-106">\<binding></span></span>  
<span data-ttu-id="9bca5-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="9bca5-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bca5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bca5-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bca5-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9bca5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9bca5-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9bca5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bca5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9bca5-111">Attributes</span></span>  
  
|<span data-ttu-id="9bca5-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9bca5-112">Attribute</span></span>|<span data-ttu-id="9bca5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9bca5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bca5-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="9bca5-114">maxReadPoolSize</span></span>|<span data-ttu-id="9bca5-115">Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="9bca5-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="9bca5-116">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="9bca5-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9bca5-117">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="9bca5-117">The default is 64.</span></span>|  
|<span data-ttu-id="9bca5-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="9bca5-118">maxWritePoolSize</span></span>|<span data-ttu-id="9bca5-119">Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="9bca5-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="9bca5-120">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="9bca5-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9bca5-121">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="9bca5-121">The default is 16.</span></span>|  
|<span data-ttu-id="9bca5-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="9bca5-122">messageVersion</span></span>|<span data-ttu-id="9bca5-123">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9bca5-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="9bca5-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9bca5-124">Valid values are</span></span><br /><br /> <span data-ttu-id="9bca5-125">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="9bca5-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="9bca5-126">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="9bca5-126">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="9bca5-127">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="9bca5-127">The default is Soap12Addressing10.</span></span> <span data-ttu-id="9bca5-128">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="9bca5-128">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="9bca5-129">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="9bca5-129">writeEncoding</span></span>|<span data-ttu-id="9bca5-130">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="9bca5-130">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9bca5-131">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9bca5-131">Valid values are</span></span><br /><br /> <span data-ttu-id="9bca5-132">-   UnicodeFffeTextEncoding: Unicode BigEndian z kodowaniem</span><span class="sxs-lookup"><span data-stu-id="9bca5-132">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="9bca5-133">-   Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="9bca5-133">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="9bca5-134">-   Utf8TextEncoding: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="9bca5-134">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9bca5-135">The default is Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="9bca5-135">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="9bca5-136">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="9bca5-136">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bca5-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9bca5-137">Child Elements</span></span>  
  
|<span data-ttu-id="9bca5-138">Element</span><span class="sxs-lookup"><span data-stu-id="9bca5-138">Element</span></span>|<span data-ttu-id="9bca5-139">Opis</span><span class="sxs-lookup"><span data-stu-id="9bca5-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bca5-140">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="9bca5-140">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="9bca5-141">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="9bca5-141">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9bca5-142">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="9bca5-142">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bca5-143">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9bca5-143">Parent Elements</span></span>  
  
|<span data-ttu-id="9bca5-144">Element</span><span class="sxs-lookup"><span data-stu-id="9bca5-144">Element</span></span>|<span data-ttu-id="9bca5-145">Opis</span><span class="sxs-lookup"><span data-stu-id="9bca5-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bca5-146">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9bca5-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9bca5-147">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9bca5-147">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bca5-148">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bca5-148">Remarks</span></span>  
 <span data-ttu-id="9bca5-149">Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="9bca5-149">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="9bca5-150">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="9bca5-150">Decoding is the reverse process.</span></span> <span data-ttu-id="9bca5-151">Windows Communication Foundation (WCF) obejmuje trzy typy kodowania dla protokołu SOAP wiadomości: Tekst pliku binarnego i mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="9bca5-151">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="9bca5-152">Kodowanie tekstu reprezentowany przez `textMessageEncoding` element jest najbardziej elementy mogły współdziałać, ale co najmniej wydajne kodera komunikatów XML.</span><span class="sxs-lookup"><span data-stu-id="9bca5-152">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="9bca5-153">Koder tekstu tworzy oparte na tekście wiadomości na łączu.</span><span class="sxs-lookup"><span data-stu-id="9bca5-153">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="9bca5-154">Komunikaty generowane przez ten koder nadają się dla protokołu WS-\* na podstawie międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="9bca5-154">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="9bca5-155">Klient usługi sieci Web lub usługa sieci Web zazwyczaj może zrozumieć tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="9bca5-155">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="9bca5-156">Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="9bca5-156">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bca5-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bca5-157">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9bca5-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bca5-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="9bca5-159">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="9bca5-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="9bca5-160">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="9bca5-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="9bca5-161">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9bca5-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9bca5-162">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9bca5-162">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9bca5-163">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9bca5-163">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9bca5-164">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9bca5-164">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
