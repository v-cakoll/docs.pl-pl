---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736219"
---
# \<textMessageEncoding>
<span data-ttu-id="3d898-101">Określa kodowanie znaków i przechowywanie wersji komunikatów używanych w przypadku tekstowych wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="3d898-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="3d898-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d898-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d898-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3d898-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3d898-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3d898-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d898-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3d898-105">Attributes</span></span>  
  
|<span data-ttu-id="3d898-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3d898-106">Attribute</span></span>|<span data-ttu-id="3d898-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3d898-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d898-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="3d898-108">maxReadPoolSize</span></span>|<span data-ttu-id="3d898-109">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="3d898-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="3d898-110">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="3d898-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3d898-111">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="3d898-111">The default is 64.</span></span>|  
|<span data-ttu-id="3d898-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="3d898-112">maxWritePoolSize</span></span>|<span data-ttu-id="3d898-113">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="3d898-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="3d898-114">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="3d898-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3d898-115">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="3d898-115">The default is 16.</span></span>|  
|<span data-ttu-id="3d898-116">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="3d898-116">messageVersion</span></span>|<span data-ttu-id="3d898-117">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="3d898-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3d898-118">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="3d898-118">Valid values are</span></span><br /><br /> <span data-ttu-id="3d898-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="3d898-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="3d898-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="3d898-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="3d898-121">- Soap11</span><span class="sxs-lookup"><span data-stu-id="3d898-121">-   Soap11</span></span><br /><span data-ttu-id="3d898-122">- Soap12</span><span class="sxs-lookup"><span data-stu-id="3d898-122">-  Soap12</span></span><br /><br /><span data-ttu-id="3d898-123">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="3d898-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="3d898-124">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="3d898-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="3d898-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="3d898-125">writeEncoding</span></span>|<span data-ttu-id="3d898-126">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3d898-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3d898-127">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="3d898-127">Valid values are</span></span><br /><br /> <span data-ttu-id="3d898-128">-UnicodeFffeTextEncoding: kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="3d898-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="3d898-129">-Utf16TextEncoding: kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="3d898-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="3d898-130">-Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="3d898-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3d898-131">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="3d898-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="3d898-132">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="3d898-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d898-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3d898-133">Child Elements</span></span>  
  
|<span data-ttu-id="3d898-134">Element</span><span class="sxs-lookup"><span data-stu-id="3d898-134">Element</span></span>|<span data-ttu-id="3d898-135">Opis</span><span class="sxs-lookup"><span data-stu-id="3d898-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="3d898-136">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3d898-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3d898-137">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="3d898-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d898-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3d898-138">Parent Elements</span></span>  
  
|<span data-ttu-id="3d898-139">Element</span><span class="sxs-lookup"><span data-stu-id="3d898-139">Element</span></span>|<span data-ttu-id="3d898-140">Opis</span><span class="sxs-lookup"><span data-stu-id="3d898-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3d898-141">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3d898-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d898-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d898-142">Remarks</span></span>  
 <span data-ttu-id="3d898-143">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="3d898-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="3d898-144">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="3d898-144">Decoding is the reverse process.</span></span> <span data-ttu-id="3d898-145">Windows Communication Foundation (WCF) zawiera trzy typy kodowania komunikatów protokołu SOAP: tekst, binarny i mechanizm optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="3d898-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="3d898-146">Kodowanie tekstu reprezentowane przez `textMessageEncoding` element to najbardziej interoperacyjny, ale najmniej wydajny koder dla wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="3d898-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="3d898-147">Koder tekstowy tworzy wiadomości tekstowe w sieci.</span><span class="sxs-lookup"><span data-stu-id="3d898-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="3d898-148">Komunikaty generowane przez ten koder są odpowiednie dla międzyoperacyjności opartego na protokole WS-\*.</span><span class="sxs-lookup"><span data-stu-id="3d898-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="3d898-149">Usługa sieci Web lub klient usługi sieci Web może ogólnie zrozumieć tekst XML.</span><span class="sxs-lookup"><span data-stu-id="3d898-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="3d898-150">Jednak przesyłanie dużych bloków danych binarnych jako tekstu jest najmniejszą efektywną metodą kodowania wiadomości XML.</span><span class="sxs-lookup"><span data-stu-id="3d898-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d898-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d898-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="3d898-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d898-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="3d898-153">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="3d898-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="3d898-154">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="3d898-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="3d898-155">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3d898-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3d898-156">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="3d898-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3d898-157">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="3d898-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
