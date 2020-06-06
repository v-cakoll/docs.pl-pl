---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738837"
---
# \<mtomMessageEncoding>
<span data-ttu-id="8bdce-101">Określa kodowanie i przechowywanie wersji komunikatów na podstawie komunikatów opartych na mechanizmie optymalizacji transmisji wiadomości (MTOM) protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8bdce-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="8bdce-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bdce-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bdce-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8bdce-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8bdce-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8bdce-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bdce-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8bdce-105">Attributes</span></span>  
  
|<span data-ttu-id="8bdce-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8bdce-106">Attribute</span></span>|<span data-ttu-id="8bdce-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8bdce-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bdce-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8bdce-108">maxBufferSize</span></span>|<span data-ttu-id="8bdce-109">Liczba całkowita określająca maksymalny rozmiar buforu, który może być używany.</span><span class="sxs-lookup"><span data-stu-id="8bdce-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="8bdce-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8bdce-110">maxReadPoolSize</span></span>|<span data-ttu-id="8bdce-111">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="8bdce-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="8bdce-112">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="8bdce-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8bdce-113">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="8bdce-113">The default is 64.</span></span>|  
|<span data-ttu-id="8bdce-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8bdce-114">maxWritePoolSize</span></span>|<span data-ttu-id="8bdce-115">Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="8bdce-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="8bdce-116">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="8bdce-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="8bdce-117">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="8bdce-117">The default is 16.</span></span>|  
|<span data-ttu-id="8bdce-118">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="8bdce-118">messageVersion</span></span>|<span data-ttu-id="8bdce-119">Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania.</span><span class="sxs-lookup"><span data-stu-id="8bdce-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="8bdce-120">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="8bdce-120">Valid values are</span></span><br /><br /> <span data-ttu-id="8bdce-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="8bdce-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="8bdce-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="8bdce-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="8bdce-123">Wartość domyślna to Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="8bdce-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="8bdce-124">Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion> .</span><span class="sxs-lookup"><span data-stu-id="8bdce-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="8bdce-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="8bdce-125">writeEncoding</span></span>|<span data-ttu-id="8bdce-126">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="8bdce-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="8bdce-127">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="8bdce-127">Valid values are</span></span><br /><br /> <span data-ttu-id="8bdce-128">-UnicodeFffeTextEncoding: kodowanie Unicode BigEndian</span><span class="sxs-lookup"><span data-stu-id="8bdce-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="8bdce-129">-Utf16TextEncoding: kodowanie Unicode</span><span class="sxs-lookup"><span data-stu-id="8bdce-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="8bdce-130">-Utf8TextEncoding: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="8bdce-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="8bdce-131">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="8bdce-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="8bdce-132">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="8bdce-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bdce-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8bdce-133">Child Elements</span></span>  
  
|<span data-ttu-id="8bdce-134">Element</span><span class="sxs-lookup"><span data-stu-id="8bdce-134">Element</span></span>|<span data-ttu-id="8bdce-135">Opis</span><span class="sxs-lookup"><span data-stu-id="8bdce-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="8bdce-136">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8bdce-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8bdce-137">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="8bdce-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8bdce-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8bdce-138">Parent Elements</span></span>  
  
|<span data-ttu-id="8bdce-139">Element</span><span class="sxs-lookup"><span data-stu-id="8bdce-139">Element</span></span>|<span data-ttu-id="8bdce-140">Opis</span><span class="sxs-lookup"><span data-stu-id="8bdce-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8bdce-141">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="8bdce-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bdce-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bdce-142">Remarks</span></span>  
 <span data-ttu-id="8bdce-143">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bdce-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="8bdce-144">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="8bdce-144">Decoding is the reverse process.</span></span> <span data-ttu-id="8bdce-145">Windows Communication Foundation (WCF) zawiera trzy typy kodowania komunikatów protokołu SOAP: tekst, binarny i mechanizm optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8bdce-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="8bdce-146">`MtomMessageEncoding`Element określa kodowanie znaków i przechowywanie wersji komunikatów oraz inne ustawienia używane w przypadku komunikatów przy użyciu kodowania mechanizmu optymalizacji transmisji komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="8bdce-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="8bdce-147">MTOM to wydajna technologia przesyłania danych binarnych w komunikatach programu WCF.</span><span class="sxs-lookup"><span data-stu-id="8bdce-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="8bdce-148">Koder MTOM próbuje utworzyć balans między wydajnością i współdziałaniem.</span><span class="sxs-lookup"><span data-stu-id="8bdce-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="8bdce-149">Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich jako-is, bez konwersji do formatu zakodowanego algorytmem Base64.</span><span class="sxs-lookup"><span data-stu-id="8bdce-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bdce-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bdce-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="8bdce-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bdce-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="8bdce-152">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="8bdce-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="8bdce-153">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="8bdce-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="8bdce-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8bdce-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8bdce-155">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="8bdce-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8bdce-156">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="8bdce-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
