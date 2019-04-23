---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: e02ed6ef79fcf52bbe9c33bd9b36a14113e19d1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228383"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="a72fa-101">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="a72fa-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="a72fa-102">Definiuje koder komunikatu binarnego, który koduje komunikatów Windows Communication Foundation (WCF) w pliku binarnego podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="a72fa-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="a72fa-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a72fa-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a72fa-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a72fa-104">\<bindings></span></span>  
<span data-ttu-id="a72fa-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a72fa-105">\<customBinding></span></span>  
<span data-ttu-id="a72fa-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a72fa-106">\<binding></span></span>  
<span data-ttu-id="a72fa-107">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="a72fa-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a72fa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a72fa-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a72fa-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a72fa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a72fa-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a72fa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a72fa-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a72fa-111">Attributes</span></span>  
  
|<span data-ttu-id="a72fa-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a72fa-112">Attribute</span></span>|<span data-ttu-id="a72fa-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a72fa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a72fa-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a72fa-114">maxReadPoolSize</span></span>|<span data-ttu-id="a72fa-115">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="a72fa-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a72fa-116">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="a72fa-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a72fa-117">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="a72fa-117">The default is 64.</span></span>|  
|<span data-ttu-id="a72fa-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="a72fa-118">maxSessionSize</span></span>|<span data-ttu-id="a72fa-119">Dodatnia liczba całkowita, określająca rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="a72fa-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="a72fa-120">Bufor większe zwiększa kodowania szybkości, kosztem rozmiar zestawu roboczego.</span><span class="sxs-lookup"><span data-stu-id="a72fa-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="a72fa-121">Wartość domyślna to 2048.</span><span class="sxs-lookup"><span data-stu-id="a72fa-121">The default is 2048.</span></span>|  
|<span data-ttu-id="a72fa-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a72fa-122">maxWritePoolSize</span></span>|<span data-ttu-id="a72fa-123">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="a72fa-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a72fa-124">Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy.</span><span class="sxs-lookup"><span data-stu-id="a72fa-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a72fa-125">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="a72fa-125">The default is 16.</span></span>|  
|<span data-ttu-id="a72fa-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a72fa-126">messageVersion</span></span>|<span data-ttu-id="a72fa-127">Określa komunikat protokołu SOAP i WS-Addressing wersje, które są używane lub przewiduje.</span><span class="sxs-lookup"><span data-stu-id="a72fa-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a72fa-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a72fa-128">Child Elements</span></span>  
  
|<span data-ttu-id="a72fa-129">Element</span><span class="sxs-lookup"><span data-stu-id="a72fa-129">Element</span></span>|<span data-ttu-id="a72fa-130">Opis</span><span class="sxs-lookup"><span data-stu-id="a72fa-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a72fa-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a72fa-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a72fa-132">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="a72fa-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a72fa-133">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a72fa-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a72fa-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a72fa-134">Parent Elements</span></span>  
  
|<span data-ttu-id="a72fa-135">Element</span><span class="sxs-lookup"><span data-stu-id="a72fa-135">Element</span></span>|<span data-ttu-id="a72fa-136">Opis</span><span class="sxs-lookup"><span data-stu-id="a72fa-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a72fa-137">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a72fa-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a72fa-138">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a72fa-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a72fa-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a72fa-139">Remarks</span></span>  
 <span data-ttu-id="a72fa-140">Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów.</span><span class="sxs-lookup"><span data-stu-id="a72fa-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a72fa-141">Dekodowanie jest procesu.</span><span class="sxs-lookup"><span data-stu-id="a72fa-141">Decoding is the reverse process.</span></span> <span data-ttu-id="a72fa-142">Windows Communication Foundation (WCF) obejmuje trzy typy kodowania dla protokołu SOAP wiadomości: Tekst pliku binarnego i mechanizmu optymalizacji transmisji wiadomości (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a72fa-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a72fa-143">`binaryMessageEncoding` Element określa Format binarny platformy .NET dla formatu XML i opcji, aby określić kodowanie znaków i wersji protokołu SOAP i WS-Addressing ma być używany.</span><span class="sxs-lookup"><span data-stu-id="a72fa-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="a72fa-144">Koder komunikatu binarnego koduje komunikatów Windows Communication Foundation (WCF) w pliku binarnego podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="a72fa-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="a72fa-145">Podczas tego kodowania skutkuje bardzo szybkie transmisję wiadomości, współdziałanie oparte na WS-\* standardów zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="a72fa-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a72fa-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="a72fa-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a72fa-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a72fa-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="a72fa-148">Kodowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="a72fa-148">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="a72fa-149">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="a72fa-149">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="a72fa-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a72fa-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a72fa-151">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a72fa-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a72fa-152">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a72fa-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a72fa-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a72fa-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
