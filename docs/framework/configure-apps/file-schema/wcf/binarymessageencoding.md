---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739072"
---
# \<binaryMessageEncoding>
<span data-ttu-id="f911d-101">Definiuje binarny koder komunikatów, który koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.</span><span class="sxs-lookup"><span data-stu-id="f911d-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="f911d-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f911d-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f911d-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f911d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f911d-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f911d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f911d-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f911d-105">Attributes</span></span>  
  
|<span data-ttu-id="f911d-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f911d-106">Attribute</span></span>|<span data-ttu-id="f911d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f911d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f911d-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f911d-108">maxReadPoolSize</span></span>|<span data-ttu-id="f911d-109">Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="f911d-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="f911d-110">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="f911d-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f911d-111">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="f911d-111">The default is 64.</span></span>|  
|<span data-ttu-id="f911d-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="f911d-112">maxSessionSize</span></span>|<span data-ttu-id="f911d-113">Dodatnia liczba całkowita, która ustawia rozmiar (w bajtach) bufora używanego do kodowania.</span><span class="sxs-lookup"><span data-stu-id="f911d-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="f911d-114">Większy bufor zwiększa szybkość kodowania przy kosztach rozmiaru zestawu roboczego.</span><span class="sxs-lookup"><span data-stu-id="f911d-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="f911d-115">Wartość domyślna to 2048.</span><span class="sxs-lookup"><span data-stu-id="f911d-115">The default is 2048.</span></span>|  
|<span data-ttu-id="f911d-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f911d-116">maxWritePoolSize</span></span>|<span data-ttu-id="f911d-117">Liczba całkowita, która określa, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="f911d-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="f911d-118">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="f911d-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f911d-119">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="f911d-119">The default is 16.</span></span>|  
|<span data-ttu-id="f911d-120">Element MessageVersion</span><span class="sxs-lookup"><span data-stu-id="f911d-120">messageVersion</span></span>|<span data-ttu-id="f911d-121">Określa komunikat protokołu SOAP i wersje WS-Addressing, które są używane lub oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="f911d-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f911d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f911d-122">Child Elements</span></span>  
  
|<span data-ttu-id="f911d-123">Element</span><span class="sxs-lookup"><span data-stu-id="f911d-123">Element</span></span>|<span data-ttu-id="f911d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f911d-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="f911d-125">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f911d-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f911d-126">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="f911d-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f911d-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f911d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f911d-128">Element</span><span class="sxs-lookup"><span data-stu-id="f911d-128">Element</span></span>|<span data-ttu-id="f911d-129">Opis</span><span class="sxs-lookup"><span data-stu-id="f911d-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f911d-130">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f911d-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f911d-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f911d-131">Remarks</span></span>  
 <span data-ttu-id="f911d-132">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="f911d-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="f911d-133">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="f911d-133">Decoding is the reverse process.</span></span> <span data-ttu-id="f911d-134">Windows Communication Foundation (WCF) zawiera trzy typy kodowania komunikatów protokołu SOAP: tekst, binarny i mechanizm optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="f911d-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="f911d-135">`binaryMessageEncoding`Element określa format binarny platformy .NET dla języka XML i zawiera opcje umożliwiające określenie kodowania znaków oraz wersji protokołu SOAP i WS-Addressing, która ma zostać użyta.</span><span class="sxs-lookup"><span data-stu-id="f911d-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="f911d-136">Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.</span><span class="sxs-lookup"><span data-stu-id="f911d-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="f911d-137">Chociaż to kodowanie skutkuje bardzo szybką transmisją komunikatów, współpraca oparta na standardach protokołu WS-\* zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="f911d-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f911d-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="f911d-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f911d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f911d-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="f911d-140">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="f911d-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="f911d-141">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="f911d-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="f911d-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f911d-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f911d-143">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f911d-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f911d-144">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f911d-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
