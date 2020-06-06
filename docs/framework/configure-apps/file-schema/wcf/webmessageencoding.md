---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 4aa87acaf9080959ba8b53e3ec3216314dc745b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732582"
---
# \<webMessageEncoding>
<span data-ttu-id="f378d-101">Umożliwia kodowanie komunikatów XML, JavaScript Object Notation (JSON) i "nieprzetworzony" zawartość binarną, która ma zostać odczytana i zapisywana w przypadku użycia w powiązaniu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f378d-101">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="f378d-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f378d-102">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f378d-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f378d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f378d-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f378d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f378d-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f378d-105">Attributes</span></span>  
  
|<span data-ttu-id="f378d-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f378d-106">Attribute</span></span>|<span data-ttu-id="f378d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f378d-107">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="f378d-108">Liczba wiadomości, które można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="f378d-108">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="f378d-109">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="f378d-109">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f378d-110">Wartość domyślna to 64 czytników dla każdego kodera wewnętrznego (text, JSON i "RAW").</span><span class="sxs-lookup"><span data-stu-id="f378d-110">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="f378d-111">Zwiększenie tej liczby powoduje zwiększenie zużycia pamięci, ale przygotowuje koder do rozpatruje nagłe rozerwanie komunikatów przychodzących, ponieważ może używać czytelników z puli, która została już utworzona, zamiast tworzyć nowe.</span><span class="sxs-lookup"><span data-stu-id="f378d-111">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="f378d-112">Ilość komunikatów, które można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="f378d-112">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="f378d-113">Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym.</span><span class="sxs-lookup"><span data-stu-id="f378d-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f378d-114">Wartość domyślna to 16 modułów zapisujących dla każdego kodera wewnętrznego (text, JSON i "RAW").</span><span class="sxs-lookup"><span data-stu-id="f378d-114">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="f378d-115">Zwiększenie tej liczby powoduje zwiększenie zużycia pamięci, ale przygotowuje koder do rozpatruje nagłe rozerwanie komunikatów wychodzących, ponieważ może korzystać z autorów z puli, która została już utworzona, zamiast tworzyć nowe.</span><span class="sxs-lookup"><span data-stu-id="f378d-115">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="f378d-116">Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="f378d-116">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f378d-117">Prawidłowe wartości:</span><span class="sxs-lookup"><span data-stu-id="f378d-117">Valid values are:</span></span><br /><br /> <span data-ttu-id="f378d-118">-UnicodeFffeTextEncoding: kodowanie Unicode big endian.</span><span class="sxs-lookup"><span data-stu-id="f378d-118">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="f378d-119">-Utf16TextEncoding: kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="f378d-119">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="f378d-120">-Utf8TextEncoding: kodowanie 8-bitowe.</span><span class="sxs-lookup"><span data-stu-id="f378d-120">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="f378d-121">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="f378d-121">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="f378d-122">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="f378d-122">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f378d-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f378d-123">Child Elements</span></span>  
  
|<span data-ttu-id="f378d-124">Element</span><span class="sxs-lookup"><span data-stu-id="f378d-124">Element</span></span>|<span data-ttu-id="f378d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f378d-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="f378d-126">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f378d-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f378d-127">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="f378d-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f378d-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f378d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f378d-129">Element</span><span class="sxs-lookup"><span data-stu-id="f378d-129">Element</span></span>|<span data-ttu-id="f378d-130">Opis</span><span class="sxs-lookup"><span data-stu-id="f378d-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f378d-131">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f378d-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f378d-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f378d-132">Remarks</span></span>  
 <span data-ttu-id="f378d-133">Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów.</span><span class="sxs-lookup"><span data-stu-id="f378d-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="f378d-134">Dekodowanie jest procesem wycofywania.</span><span class="sxs-lookup"><span data-stu-id="f378d-134">Decoding is the reverse process.</span></span> <span data-ttu-id="f378d-135">Procesy te wymagają specyfikacji kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="f378d-135">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="f378d-136">`webMessageEncoding`Element działa przez delegowanie do serii koderów wewnętrznych w celu obsługi kodowania XML i JSON oraz "RAW" danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="f378d-136">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="f378d-137">To delegowanie odbywa się za pomocą złożonego kodera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f378d-137">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="f378d-138">Ten element powiązania i jego koder złożony są używane do sterowania kodowaniem w scenariuszach, które nie korzystają z komunikatów SOAP używanych przez `webHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="f378d-138">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="f378d-139">Te scenariusze obejmują "zwykłe stare XML" (POX), przenoszenie stanu reprezentacji (REST), Really Simple Syndication (RSS) i Atom Syndication oraz asynchroniczne skrypty JavaScript i XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="f378d-139">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="f378d-140">Koder komunikatu złożonego nie obsługuje protokołu SOAP ani WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="f378d-140">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="f378d-141">Element Binding można skonfigurować przy użyciu kodowania znaków zapisu za pomocą `writeEncoding` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f378d-141">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="f378d-142">Podana <xref:System.Text.Encoding> wartość określa zachowanie przy zapisie dla przypadków JSON i tekstowych XML.</span><span class="sxs-lookup"><span data-stu-id="f378d-142">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="f378d-143">W przypadku odczytu wszystkie prawidłowe kodowanie komunikatów i kodowanie tekstu są zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="f378d-143">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="f378d-144">`maxReadPoolSize`i `maxWritePoolSize` można również użyć, aby ustawić maksymalną liczbę czytelników i autorów, które mają być odpowiednio przydzieloną.</span><span class="sxs-lookup"><span data-stu-id="f378d-144">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="f378d-145">Domyślnie przydzielono 64 czytników i 16 składników zapisywania.</span><span class="sxs-lookup"><span data-stu-id="f378d-145">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="f378d-146">Domyślne ograniczenia złożoności są również ustawiane za pomocą [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) elementu, aby chronić przed atakami typu "odmowa usługi" (DOS), które próbują użyć złożoności komunikatów do powiązania zasobów przetwarzania punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f378d-146">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f378d-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="f378d-147">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f378d-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f378d-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="f378d-149">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="f378d-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="f378d-150">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="f378d-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="f378d-151">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f378d-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f378d-152">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f378d-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f378d-153">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f378d-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
