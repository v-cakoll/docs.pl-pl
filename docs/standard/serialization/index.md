---
title: Serializacja w .NET
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 1f90a128ef6b29acbd315beae7aaaf1d1b78a62b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638844"
---
# <a name="serialization-in-net"></a><span data-ttu-id="f7d2f-102">Serializacja w .NET</span><span class="sxs-lookup"><span data-stu-id="f7d2f-102">Serialization in .NET</span></span>
<span data-ttu-id="f7d2f-103">Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="f7d2f-104">Uzupełnienia do serializacji jest deserializacji, który konwertuje strumienia na obiekt.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="f7d2f-105">Razem te procesy umożliwiają danych można łatwo przechowywane i przekazywane.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="f7d2f-106">.NET oferuje dwa serializacji technologii:</span><span class="sxs-lookup"><span data-stu-id="f7d2f-106">.NET features two serialization technologies:</span></span>  
  
- <span data-ttu-id="f7d2f-107">Serializacja binarna zachowuje wierności typu, co ułatwia zachowania stanu obiektu między wywołań różnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="f7d2f-108">Na przykład można udostępniać obiektu między różnymi aplikacjami, szeregując go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="f7d2f-109">Można serializować obiektu w strumieniu na dysku w pamięci, za pośrednictwem sieci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="f7d2f-110">Zdalne używa serializacji do przekazania obiektów "przez wartość" z jednej domeny komputera lub aplikacji do innego.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="f7d2f-111">Serializacji XML serializuje tylko właściwości publiczne i pola i nie zostaną zachowane wierności typu.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="f7d2f-112">Jest to przydatne, jeśli chcesz podać lub zużywać danych nie ograniczając aplikacji, która używa tych danych.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="f7d2f-113">Ponieważ kod XML jest otwarty standard, jest atrakcyjny wybór udostępnianie danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="f7d2f-114">Podobnie protokołu SOAP jest otwarty standard, co pozwala na wybór atrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7d2f-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f7d2f-115">In This Section</span></span>  
[<span data-ttu-id="f7d2f-116">Serializacja — instrukcje</span><span class="sxs-lookup"><span data-stu-id="f7d2f-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="f7d2f-117">Zawiera także łącza do tematów instrukcje zawarte w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="f7d2f-118">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="f7d2f-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="f7d2f-119">Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="f7d2f-120">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="f7d2f-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="f7d2f-121">Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="f7d2f-122">Narzędzia do serializacji</span><span class="sxs-lookup"><span data-stu-id="f7d2f-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="f7d2f-123">Te narzędzia ułatwiają tworzenie kodu serializacji.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="f7d2f-124">Przykłady serializacji</span><span class="sxs-lookup"><span data-stu-id="f7d2f-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="f7d2f-125">Przykłady pokazują, jak to zrobić serializacji.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="f7d2f-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="f7d2f-126">Reference</span></span>
<span data-ttu-id="f7d2f-127"><xref:System.Runtime.Serialization> Zawiera klasy, które mogą służyć do serializacji i deserializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="f7d2f-128">Zawiera klasy, których można użyć do wykonywania serializacji obiektów w dokumentach formatu XML lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="f7d2f-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>
