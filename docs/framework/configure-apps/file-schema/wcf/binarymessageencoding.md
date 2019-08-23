---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919795"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="435e9-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="435e9-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="435e9-102">Definiuje binarny koder komunikatów, który koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.</span><span class="sxs-lookup"><span data-stu-id="435e9-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="435e9-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="435e9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="435e9-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="435e9-104">\<bindings></span></span>  
<span data-ttu-id="435e9-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="435e9-105">\<customBinding></span></span>  
<span data-ttu-id="435e9-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="435e9-106">\<binding></span></span>  
<span data-ttu-id="435e9-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="435e9-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="435e9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="435e9-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="435e9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="435e9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="435e9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="435e9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="435e9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="435e9-111">Attributes</span></span>  
  
|<span data-ttu-id="435e9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="435e9-112">Attribute</span></span>|<span data-ttu-id="435e9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="435e9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="435e9-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="435e9-114">maxReadPoolSize</span></span>|<span data-ttu-id="435e9-115">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="435e9-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="435e9-116">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="435e9-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="435e9-117">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="435e9-117">The default is 64.</span></span>|  
|<span data-ttu-id="435e9-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="435e9-118">maxSessionSize</span></span>|<span data-ttu-id="435e9-119">Dodatnia liczba całkowita, która ustawia rozmiar (w bajtach) bufora używanego do kodowania.</span><span class="sxs-lookup"><span data-stu-id="435e9-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="435e9-120">Większy bufor zwiększa szybkość kodowania przy kosztach rozmiaru zestawu roboczego.</span><span class="sxs-lookup"><span data-stu-id="435e9-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="435e9-121">Wartość domyślna to 2048.</span><span class="sxs-lookup"><span data-stu-id="435e9-121">The default is 2048.</span></span>|  
|<span data-ttu-id="435e9-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="435e9-122">maxWritePoolSize</span></span>|<span data-ttu-id="435e9-123">Liczba całkowita, która określa, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="435e9-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="435e9-124">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="435e9-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="435e9-125">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="435e9-125">The default is 16.</span></span>|  
|<span data-ttu-id="435e9-126">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="435e9-126">messageVersion</span></span>|<span data-ttu-id="435e9-127">Określa komunikat protokołu SOAP i wersje WS-Addressing, które są używane lub oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="435e9-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="435e9-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="435e9-128">Child Elements</span></span>  
  
|<span data-ttu-id="435e9-129">Element</span><span class="sxs-lookup"><span data-stu-id="435e9-129">Element</span></span>|<span data-ttu-id="435e9-130">Opis</span><span class="sxs-lookup"><span data-stu-id="435e9-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="435e9-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="435e9-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="435e9-132">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="435e9-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="435e9-133">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="435e9-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="435e9-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="435e9-134">Parent Elements</span></span>  
  
|<span data-ttu-id="435e9-135">Element</span><span class="sxs-lookup"><span data-stu-id="435e9-135">Element</span></span>|<span data-ttu-id="435e9-136">Opis</span><span class="sxs-lookup"><span data-stu-id="435e9-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="435e9-137">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="435e9-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="435e9-138">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="435e9-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="435e9-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="435e9-139">Remarks</span></span>  
 <span data-ttu-id="435e9-140">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="435e9-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="435e9-141">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="435e9-141">Decoding is the reverse process.</span></span> <span data-ttu-id="435e9-142">Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla komunikatów SOAP: Mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM).</span><span class="sxs-lookup"><span data-stu-id="435e9-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="435e9-143">`binaryMessageEncoding` Element określa format binarny platformy .NET dla języka XML i zawiera opcje umożliwiające określenie kodowania znaków oraz wersji protokołu SOAP i WS-Addressing, która ma zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="435e9-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="435e9-144">Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.</span><span class="sxs-lookup"><span data-stu-id="435e9-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="435e9-145">Chociaż to kodowanie skutkuje bardzo szybką transmisją komunikatów, współpraca oparta na standardach protokołu WS-\* zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="435e9-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="435e9-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="435e9-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="435e9-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="435e9-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="435e9-148">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="435e9-148">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="435e9-149">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="435e9-149">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="435e9-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="435e9-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="435e9-151">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="435e9-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="435e9-152">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="435e9-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="435e9-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="435e9-153">\<customBinding></span></span>](custombinding.md)
