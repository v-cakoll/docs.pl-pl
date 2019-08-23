---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: a1d776730053cd6af3c930a33e13582a8906c4d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940398"
---
# <a name="webmessageencoding"></a><span data-ttu-id="b63a4-101">\<webMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="b63a4-101">\<webMessageEncoding></span></span>
<span data-ttu-id="b63a4-102">Umożliwia kodowanie komunikatów XML, JavaScript Object Notation (JSON) i "nieprzetworzony" zawartość binarną, która ma zostać odczytana i zapisywana w przypadku użycia w powiązaniu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b63a4-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="b63a4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b63a4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b63a4-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="b63a4-104">\<bindings></span></span>  
<span data-ttu-id="b63a4-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b63a4-105">\<customBinding></span></span>  
<span data-ttu-id="b63a4-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b63a4-106">\<binding></span></span>  
<span data-ttu-id="b63a4-107">\<webMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="b63a4-107">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b63a4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b63a4-108">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b63a4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b63a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b63a4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b63a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b63a4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b63a4-111">Attributes</span></span>  
  
|<span data-ttu-id="b63a4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b63a4-112">Attribute</span></span>|<span data-ttu-id="b63a4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b63a4-113">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="b63a4-114">Liczba wiadomości, które można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="b63a4-114">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="b63a4-115">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="b63a4-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b63a4-116">Wartość domyślna to 64 czytników dla każdego kodera wewnętrznego (text, JSON i "RAW").</span><span class="sxs-lookup"><span data-stu-id="b63a4-116">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="b63a4-117">Zwiększenie tej liczby powoduje zwiększenie zużycia pamięci, ale przygotowuje koder do rozpatruje nagłe rozerwanie komunikatów przychodzących, ponieważ może używać czytelników z puli, która została już utworzona, zamiast tworzyć nowe.</span><span class="sxs-lookup"><span data-stu-id="b63a4-117">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="b63a4-118">Ilość komunikatów, które można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="b63a4-118">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="b63a4-119">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="b63a4-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b63a4-120">Wartość domyślna to 16 modułów zapisujących dla każdego kodera wewnętrznego (text, JSON i "RAW").</span><span class="sxs-lookup"><span data-stu-id="b63a4-120">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="b63a4-121">Zwiększenie tej liczby powoduje zwiększenie zużycia pamięci, ale przygotowuje koder do rozpatruje nagłe rozerwanie komunikatów wychodzących, ponieważ może korzystać z autorów z puli, która została już utworzona, zamiast tworzyć nowe.</span><span class="sxs-lookup"><span data-stu-id="b63a4-121">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="b63a4-122">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="b63a4-122">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b63a4-123">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="b63a4-123">Valid values are:</span></span><br /><br /> <span data-ttu-id="b63a4-124">- UnicodeFffeTextEncoding: Kodowanie Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="b63a4-124">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="b63a4-125">- Utf16TextEncoding: Kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="b63a4-125">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="b63a4-126">-   Utf8TextEncoding: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="b63a4-126">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b63a4-127">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="b63a4-127">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="b63a4-128">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b63a4-128">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b63a4-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b63a4-129">Child Elements</span></span>  
  
|<span data-ttu-id="b63a4-130">Element</span><span class="sxs-lookup"><span data-stu-id="b63a4-130">Element</span></span>|<span data-ttu-id="b63a4-131">Opis</span><span class="sxs-lookup"><span data-stu-id="b63a4-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b63a4-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b63a4-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b63a4-133">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b63a4-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b63a4-134">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b63a4-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b63a4-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b63a4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b63a4-136">Element</span><span class="sxs-lookup"><span data-stu-id="b63a4-136">Element</span></span>|<span data-ttu-id="b63a4-137">Opis</span><span class="sxs-lookup"><span data-stu-id="b63a4-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b63a4-138">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b63a4-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b63a4-139">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b63a4-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b63a4-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b63a4-140">Remarks</span></span>  
 <span data-ttu-id="b63a4-141">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="b63a4-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="b63a4-142">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="b63a4-142">Decoding is the reverse process.</span></span> <span data-ttu-id="b63a4-143">Procesy te wymagają specyfikacji kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="b63a4-143">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="b63a4-144">`webMessageEncoding` Element działa przez delegowanie do serii koderów wewnętrznych w celu obsługi kodowania XML i JSON oraz "RAW" danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="b63a4-144">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="b63a4-145">To delegowanie odbywa się za pomocą złożonego kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b63a4-145">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="b63a4-146">Ten element powiązania i jego koder złożony są używane do sterowania kodowaniem w scenariuszach, które nie korzystają z `webHttpBinding` komunikatów SOAP używanych przez element.</span><span class="sxs-lookup"><span data-stu-id="b63a4-146">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="b63a4-147">Te scenariusze obejmują "zwykłe stare XML" (POX), przenoszenie stanu reprezentacji (REST), Really Simple Syndication (RSS) i Atom Syndication oraz asynchroniczne skrypty JavaScript i XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="b63a4-147">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="b63a4-148">Koder komunikatu złożonego nie obsługuje protokołu SOAP ani WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b63a4-148">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="b63a4-149">Element Binding można skonfigurować przy użyciu kodowania znaków zapisu za pomocą `writeEncoding` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b63a4-149">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="b63a4-150">Podana <xref:System.Text.Encoding> wartość określa zachowanie przy zapisie dla przypadków JSON i tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="b63a4-150">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="b63a4-151">W przypadku odczytu wszystkie prawidłowe kodowanie komunikatów i kodowanie tekstu są zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="b63a4-151">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="b63a4-152">`maxReadPoolSize`i `maxWritePoolSize` można również użyć, aby ustawić maksymalną liczbę czytelników i autorów, które mają być odpowiednio przydzieloną.</span><span class="sxs-lookup"><span data-stu-id="b63a4-152">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="b63a4-153">Domyślnie przydzielono 64 czytników i 16 składników zapisywania.</span><span class="sxs-lookup"><span data-stu-id="b63a4-153">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="b63a4-154">Domyślne ograniczenia dotyczące złożoności są również ustawiane za pomocą [ \<elementu readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) , aby chronić przed atakami klasy typu "odmowa usługi" (DOS), które próbują użyć złożoności komunikatów do powiązania zasobów przetwarzania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b63a4-154">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b63a4-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="b63a4-155">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b63a4-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b63a4-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="b63a4-157">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="b63a4-157">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="b63a4-158">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="b63a4-158">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="b63a4-159">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b63a4-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b63a4-160">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b63a4-160">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b63a4-161">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b63a4-161">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b63a4-162">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b63a4-162">\<customBinding></span></span>](custombinding.md)
