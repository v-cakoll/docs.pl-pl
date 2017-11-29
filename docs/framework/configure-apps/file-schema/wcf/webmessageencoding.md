---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e6257721f8b85296d4da28cc036c946f6357c11b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="89732-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="89732-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="89732-103">Włącza zwykłego tekstu XML, kodowania wiadomości notacji obiektu JavaScript (JSON) i "nieprzetworzonej" zawartości binarnej na odczyt i zapis w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] powiązania.</span><span class="sxs-lookup"><span data-stu-id="89732-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span>  
  
 <span data-ttu-id="89732-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="89732-104">\<system.serviceModel></span></span>  
<span data-ttu-id="89732-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="89732-105">\<bindings></span></span>  
<span data-ttu-id="89732-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="89732-106">\<customBinding></span></span>  
<span data-ttu-id="89732-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="89732-107">\<binding></span></span>  
<span data-ttu-id="89732-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="89732-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89732-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="89732-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89732-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89732-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89732-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="89732-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89732-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89732-112">Attributes</span></span>  
  
|<span data-ttu-id="89732-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="89732-113">Attribute</span></span>|<span data-ttu-id="89732-114">Opis</span><span class="sxs-lookup"><span data-stu-id="89732-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="89732-115">Liczba wiadomości, które można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="89732-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="89732-116">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="89732-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="89732-117">Wartość domyślna to 64 czytników dla każdego wewnętrzny koderów (tekst JSON i "nieprzetworzonej").</span><span class="sxs-lookup"><span data-stu-id="89732-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="89732-118">Zwiększenie tego numeru zużycie pamięci wzrośnie, ale przygotowuje kodera do postępowania w przypadku nagłego Seria wiadomości przychodzących, ponieważ jest w stanie używać czytników z puli, które zostały już utworzone, zamiast tworzyć nowe.</span><span class="sxs-lookup"><span data-stu-id="89732-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="89732-119">Liczba wiadomości, które można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="89732-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="89732-120">Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="89732-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="89732-121">Wartość domyślna to 16 autorów dla każdego wewnętrzny koderów (tekst JSON i "nieprzetworzonej").</span><span class="sxs-lookup"><span data-stu-id="89732-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="89732-122">Zwiększenie tego numeru zużycie pamięci wzrośnie, ale przygotowuje kodera do postępowania w przypadku nagłego seria wychodzących wiadomości, ponieważ jest w stanie używać autorów z puli, które zostały już utworzone, zamiast tworzyć nowe.</span><span class="sxs-lookup"><span data-stu-id="89732-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="89732-123">Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="89732-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="89732-124">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="89732-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="89732-125">-UnicodeFffeTextEncoding: Big Endian kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="89732-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="89732-126">-Utf16TextEncoding: Kodowanie Unicode.</span><span class="sxs-lookup"><span data-stu-id="89732-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="89732-127">-Utf8TextEncoding: 8-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="89732-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="89732-128">Wartość domyślna to Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="89732-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="89732-129">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="89732-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89732-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89732-130">Child Elements</span></span>  
  
|<span data-ttu-id="89732-131">Element</span><span class="sxs-lookup"><span data-stu-id="89732-131">Element</span></span>|<span data-ttu-id="89732-132">Opis</span><span class="sxs-lookup"><span data-stu-id="89732-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89732-133">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="89732-133">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="89732-134">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="89732-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="89732-135">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="89732-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89732-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89732-136">Parent Elements</span></span>  
  
|<span data-ttu-id="89732-137">Element</span><span class="sxs-lookup"><span data-stu-id="89732-137">Element</span></span>|<span data-ttu-id="89732-138">Opis</span><span class="sxs-lookup"><span data-stu-id="89732-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89732-139">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="89732-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="89732-140">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="89732-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89732-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89732-141">Remarks</span></span>  
 <span data-ttu-id="89732-142">Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="89732-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="89732-143">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="89732-143">Decoding is the reverse process.</span></span> <span data-ttu-id="89732-144">Te procesy wymagają specyfikacji kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="89732-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="89732-145">`webMessageEncoding` Element działa przez delegowanie do serii wewnętrzny koderów na kodowań XML i JSON zwykłego tekstu, a "" dane binarne.</span><span class="sxs-lookup"><span data-stu-id="89732-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="89732-146">To Delegowanie jest realizowane przez koder komunikatów złożonego.</span><span class="sxs-lookup"><span data-stu-id="89732-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="89732-147">Ten element powiązania i jego encoder złożone są używane do kontrolowania, kodowania w scenariuszach, które nie korzystają z protokołu SOAP wiadomości używanych przez `webHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="89732-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="89732-148">Te scenariusze obejmują "XML starego zwykły" (POX), Representational State (Transfer REST), zespolonego naprawdę proste Syndication (RSS) i Atom i asynchronicznego JavaScript i XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="89732-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="89732-149">Koder komunikatów złożonego nie obsługuje protokołu SOAP lub WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="89732-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="89732-150">Element powiązania można skonfigurować za pomocą znaku zapisu przy użyciu kodowania `writeEncoding` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="89732-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="89732-151">Podana <xref:System.Text.Encoding> wartość określa zachowanie podczas zapisu w przypadkach, JSON i XML tekstową.</span><span class="sxs-lookup"><span data-stu-id="89732-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="89732-152">Na odczyt wszelkie kodowanie prawidłowego elementu message i kodowanie tekstu jest rozpoznawany.</span><span class="sxs-lookup"><span data-stu-id="89732-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="89732-153">`maxReadPoolSize`i `maxWritePoolSize` można również ustawić maksymalną liczbę czytelników i zapisywania odpowiednio przydzielone.</span><span class="sxs-lookup"><span data-stu-id="89732-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="89732-154">Domyślnie są przydzielane 64 czytelników i 16 modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="89732-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="89732-155">Domyślne ograniczenia złożoności są również ustawiane przy użyciu [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) elementu, aby zapewnić ochronę przed klasą odmowa usługi (DOS) przed atakami opartymi na tym próbę użycia złożoności wiadomości wiązać przetwarzania punktu końcowego zasoby.</span><span class="sxs-lookup"><span data-stu-id="89732-155">Default complexity constraints are also set using the [\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89732-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="89732-156">Example</span></span>  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89732-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89732-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="89732-158">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="89732-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="89732-159">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="89732-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="89732-160">Powiązania</span><span class="sxs-lookup"><span data-stu-id="89732-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="89732-161">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="89732-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="89732-162">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="89732-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="89732-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="89732-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
