---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: feefd7fe73363b5fe1ec5658c5dc339c3d6bac57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398209"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="46a8e-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="46a8e-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="46a8e-102">Definiuje binarny koder komunikatów, który koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.</span><span class="sxs-lookup"><span data-stu-id="46a8e-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
<span data-ttu-id="46a8e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="46a8e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="46a8e-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="46a8e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="46a8e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="46a8e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="46a8e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="46a8e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="46a8e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="46a8e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="46a8e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<binaryMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="46a8e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46a8e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="46a8e-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46a8e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="46a8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="46a8e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="46a8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46a8e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="46a8e-112">Attributes</span></span>  
  
|<span data-ttu-id="46a8e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="46a8e-113">Attribute</span></span>|<span data-ttu-id="46a8e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="46a8e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46a8e-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="46a8e-115">maxReadPoolSize</span></span>|<span data-ttu-id="46a8e-116">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="46a8e-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="46a8e-117">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="46a8e-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="46a8e-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="46a8e-118">The default is 64.</span></span>|  
|<span data-ttu-id="46a8e-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="46a8e-119">maxSessionSize</span></span>|<span data-ttu-id="46a8e-120">Dodatnia liczba całkowita, która ustawia rozmiar (w bajtach) bufora używanego do kodowania.</span><span class="sxs-lookup"><span data-stu-id="46a8e-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="46a8e-121">Większy bufor zwiększa szybkość kodowania przy kosztach rozmiaru zestawu roboczego.</span><span class="sxs-lookup"><span data-stu-id="46a8e-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="46a8e-122">Wartość domyślna to 2048.</span><span class="sxs-lookup"><span data-stu-id="46a8e-122">The default is 2048.</span></span>|  
|<span data-ttu-id="46a8e-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="46a8e-123">maxWritePoolSize</span></span>|<span data-ttu-id="46a8e-124">Liczba całkowita, która określa, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="46a8e-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="46a8e-125">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="46a8e-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="46a8e-126">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="46a8e-126">The default is 16.</span></span>|  
|<span data-ttu-id="46a8e-127">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="46a8e-127">messageVersion</span></span>|<span data-ttu-id="46a8e-128">Określa komunikat protokołu SOAP i wersje WS-Addressing, które są używane lub oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="46a8e-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46a8e-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="46a8e-129">Child Elements</span></span>  
  
|<span data-ttu-id="46a8e-130">Element</span><span class="sxs-lookup"><span data-stu-id="46a8e-130">Element</span></span>|<span data-ttu-id="46a8e-131">Opis</span><span class="sxs-lookup"><span data-stu-id="46a8e-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46a8e-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46a8e-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="46a8e-133">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="46a8e-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="46a8e-134">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="46a8e-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46a8e-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="46a8e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="46a8e-136">Element</span><span class="sxs-lookup"><span data-stu-id="46a8e-136">Element</span></span>|<span data-ttu-id="46a8e-137">Opis</span><span class="sxs-lookup"><span data-stu-id="46a8e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46a8e-138">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="46a8e-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="46a8e-139">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="46a8e-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46a8e-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46a8e-140">Remarks</span></span>  
 <span data-ttu-id="46a8e-141">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="46a8e-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="46a8e-142">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="46a8e-142">Decoding is the reverse process.</span></span> <span data-ttu-id="46a8e-143">Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla komunikatów SOAP: Mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="46a8e-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="46a8e-144">`binaryMessageEncoding` Element określa format binarny platformy .NET dla języka XML i zawiera opcje umożliwiające określenie kodowania znaków oraz wersji protokołu SOAP i WS-Addressing, która ma zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="46a8e-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="46a8e-145">Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.</span><span class="sxs-lookup"><span data-stu-id="46a8e-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="46a8e-146">Chociaż to kodowanie skutkuje bardzo szybką transmisją komunikatów, współpraca oparta na standardach protokołu WS-\* zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="46a8e-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46a8e-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="46a8e-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="46a8e-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46a8e-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="46a8e-149">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="46a8e-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="46a8e-150">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="46a8e-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="46a8e-151">Powiązania</span><span class="sxs-lookup"><span data-stu-id="46a8e-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="46a8e-152">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="46a8e-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="46a8e-153">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="46a8e-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="46a8e-154">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="46a8e-154">\<customBinding></span></span>](custombinding.md)
