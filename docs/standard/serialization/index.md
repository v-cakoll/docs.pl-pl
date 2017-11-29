---
title: Serializacja w .NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c97dc9b98f90af31c86af5295a7a4ad9894b428
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serialization-in-net"></a><span data-ttu-id="29979-102">Serializacja w .NET</span><span class="sxs-lookup"><span data-stu-id="29979-102">Serialization in .NET</span></span>
<span data-ttu-id="29979-103">Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane.</span><span class="sxs-lookup"><span data-stu-id="29979-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="29979-104">Uzupełnienie serializacji jest deserializacji, które służy do obiektu strumienia.</span><span class="sxs-lookup"><span data-stu-id="29979-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="29979-105">Razem te procesy umożliwiają danych można łatwo przechowywane i przekazywane.</span><span class="sxs-lookup"><span data-stu-id="29979-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="29979-106">Usług .NET features dwie technologie serializacji:</span><span class="sxs-lookup"><span data-stu-id="29979-106">.NET features two serialization technologies:</span></span>  
  
-   <span data-ttu-id="29979-107">Serializacja binarna zachowuje wierności typów, co jest przydatne, aby zachować stan obiektu między różnymi wywołaniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29979-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="29979-108">Na przykład można udostępniać obiekt między różnymi aplikacjami, szeregując go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="29979-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="29979-109">Można serializować obiektu w strumieniu na dysku w pamięci, za pośrednictwem sieci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="29979-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="29979-110">Komunikację zdalną używa serializacji do przekazania obiektów "przez wartość" z jednej domeny komputera lub aplikacji na inny.</span><span class="sxs-lookup"><span data-stu-id="29979-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
-   <span data-ttu-id="29979-111">Serializacji XML serializuje tylko właściwości publiczne i pola i nie zostaną zachowane wierności typu.</span><span class="sxs-lookup"><span data-stu-id="29979-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="29979-112">Jest to przydatne, jeśli chcesz dostarczyć lub użyć danych bez ograniczania aplikacji korzystającej z danych.</span><span class="sxs-lookup"><span data-stu-id="29979-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="29979-113">Ponieważ kod XML jest otwarty standard, jest atrakcyjny wybór udostępnianie danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="29979-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="29979-114">Podobnie protokołu SOAP jest otwarty standard, co pozwala na wybór atrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="29979-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29979-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="29979-115">In This Section</span></span>  
[<span data-ttu-id="29979-116">Serializacja — tematy porad</span><span class="sxs-lookup"><span data-stu-id="29979-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="29979-117">Zawiera także łącza do tematów instrukcje zawarte w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="29979-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="29979-118">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="29979-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="29979-119">Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="29979-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="29979-120">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="29979-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="29979-121">Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="29979-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="29979-122">Narzędzia do serializacji</span><span class="sxs-lookup"><span data-stu-id="29979-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="29979-123">Te narzędzia ułatwiają tworzenie kodu serializacji.</span><span class="sxs-lookup"><span data-stu-id="29979-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="29979-124">Przykłady serializacji</span><span class="sxs-lookup"><span data-stu-id="29979-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="29979-125">Przykłady pokazują, jak to zrobić serializacji.</span><span class="sxs-lookup"><span data-stu-id="29979-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="29979-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="29979-126">Reference</span></span>
<span data-ttu-id="29979-127"><xref:System.Runtime.Serialization>Zawiera klasy, które mogą służyć do serializacji i deserializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="29979-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="29979-128">Zawiera klasy, których można użyć do wykonywania serializacji obiektów w dokumentach formatu XML lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="29979-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>