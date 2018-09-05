---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e684c21c0b1360a9b270214ebe7b3ad00b42657f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554503"
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="4a518-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="4a518-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="4a518-103">Określa kodowanie znaków i wiadomości versioning używany dla wiadomości tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="4a518-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="4a518-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4a518-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4a518-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4a518-105">\<bindings></span></span>  
<span data-ttu-id="4a518-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4a518-106">\<customBinding></span></span>  
<span data-ttu-id="4a518-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4a518-107">\<binding></span></span>  
<span data-ttu-id="4a518-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="4a518-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a518-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a518-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a518-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a518-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4a518-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a518-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a518-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a518-112">Attributes</span></span>  
  
|<span data-ttu-id="4a518-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a518-113">Attribute</span></span>|<span data-ttu-id="4a518-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4a518-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a518-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4a518-115">maxReadPoolSize</span></span>|<span data-ttu-id="4a518-116">Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="4a518-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4a518-117">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="4a518-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4a518-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="4a518-118">The default is 64.</span></span>|  
|<span data-ttu-id="4a518-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4a518-119">maxWritePoolSize</span></span>|<span data-ttu-id="4a518-120">Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="4a518-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4a518-121">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="4a518-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4a518-122">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="4a518-122">The default is 16.</span></span>|  
|<span data-ttu-id="4a518-123">Element messageVersion</span><span class="sxs-lookup"><span data-stu-id="4a518-123">messageVersion</span></span>|<span data-ttu-id="4a518-124">Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4a518-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4a518-125">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="4a518-125">Valid values are</span></span><br /><br /> <span data-ttu-id="4a518-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="4a518-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="4a518-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4a518-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="4a518-128">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="4a518-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4a518-129">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="4a518-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4a518-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4a518-130">writeEncoding</span></span>|<span data-ttu-id="4a518-131">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="4a518-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4a518-132">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="4a518-132">Valid values are</span></span><br /><br /> <span data-ttu-id="4a518-133">-UnicodeFffeTextEncoding: Unicode BigEndian kodowanie</span><span class="sxs-lookup"><span data-stu-id="4a518-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4a518-134">-Utf16TextEncoding: Kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="4a518-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4a518-135">-Utf8TextEncoding: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="4a518-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4a518-136">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="4a518-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4a518-137">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4a518-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a518-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a518-138">Child Elements</span></span>  
  
|<span data-ttu-id="4a518-139">Element</span><span class="sxs-lookup"><span data-stu-id="4a518-139">Element</span></span>|<span data-ttu-id="4a518-140">Opis</span><span class="sxs-lookup"><span data-stu-id="4a518-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a518-141">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="4a518-141">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4a518-142">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="4a518-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4a518-143">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4a518-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a518-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a518-144">Parent Elements</span></span>  
  
|<span data-ttu-id="4a518-145">Element</span><span class="sxs-lookup"><span data-stu-id="4a518-145">Element</span></span>|<span data-ttu-id="4a518-146">Opis</span><span class="sxs-lookup"><span data-stu-id="4a518-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a518-147">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4a518-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4a518-148">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4a518-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a518-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a518-149">Remarks</span></span>  
 <span data-ttu-id="4a518-150">Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="4a518-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4a518-151">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="4a518-151">Decoding is the reverse process.</span></span> <span data-ttu-id="4a518-152">Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla wiadomości SOAP: tekst, dane binarne i komunikat transmisji optymalizacji mechanizm (MTOM).</span><span class="sxs-lookup"><span data-stu-id="4a518-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4a518-153">Kodowanie tekstu reprezentowany przez `textMessageEncoding` element jest najbardziej elementy mogły współdziałać, ale co najmniej wydajne kodera komunikatów XML.</span><span class="sxs-lookup"><span data-stu-id="4a518-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="4a518-154">Koder tekstu tworzy oparte na tekście wiadomości na łączu.</span><span class="sxs-lookup"><span data-stu-id="4a518-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="4a518-155">Komunikaty generowane przez ten koder nadają się dla protokołu WS-\* na podstawie międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="4a518-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="4a518-156">Klient usługi sieci Web lub usługa sieci Web zazwyczaj może zrozumieć tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="4a518-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4a518-157">Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="4a518-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a518-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a518-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a518-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a518-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="4a518-160">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="4a518-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="4a518-161">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="4a518-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="4a518-162">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4a518-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4a518-163">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="4a518-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4a518-164">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="4a518-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4a518-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4a518-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
