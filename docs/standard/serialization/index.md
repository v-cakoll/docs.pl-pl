---
title: Serializacja — .NET
description: Ten artykuł zawiera informacje o technologiach serializacji platformy .NET, w tym serializacji binarnej, serializacji XML i SOAP oraz serializacji JSON.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "83377243"
---
# <a name="serialization-in-net"></a><span data-ttu-id="a6417-103">Serializacja w .NET</span><span class="sxs-lookup"><span data-stu-id="a6417-103">Serialization in .NET</span></span>

<span data-ttu-id="a6417-104">Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane.</span><span class="sxs-lookup"><span data-stu-id="a6417-104">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="a6417-105">Uzupełnienie serializacji jest deserializacji, która konwertuje strumień na obiekt.</span><span class="sxs-lookup"><span data-stu-id="a6417-105">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="a6417-106">Procesy te umożliwiają jednoczesne przechowywanie i przesyłanie danych.</span><span class="sxs-lookup"><span data-stu-id="a6417-106">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="a6417-107">Platforma .NET oferuje następujące technologie serializacji:</span><span class="sxs-lookup"><span data-stu-id="a6417-107">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="a6417-108">[Serializacja binarna](binary-serialization.md) zachowuje wierność typu, co jest przydatne do zachowania stanu obiektu między różnymi wywołaniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6417-108">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="a6417-109">Na przykład można udostępnić obiekt między różnymi aplikacjami, serializacji go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="a6417-109">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="a6417-110">Można serializować obiektu w strumieniu na dysku w pamięci, za pośrednictwem sieci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="a6417-110">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="a6417-111">Komunikacja zdalna używa serializacji do przekazywania obiektów "według wartości" z jednego komputera lub domeny aplikacji do innej.</span><span class="sxs-lookup"><span data-stu-id="a6417-111">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="a6417-112">[Serializacji XML i SOAP](xml-and-soap-serialization.md) serializować tylko właściwości publiczne i pola i nie zachowuje wierności typów.</span><span class="sxs-lookup"><span data-stu-id="a6417-112">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="a6417-113">Jest to przydatne, gdy chcesz zapewnić lub wykorzystać dane bez ograniczania aplikacji, która korzysta z danych.</span><span class="sxs-lookup"><span data-stu-id="a6417-113">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="a6417-114">Ponieważ kod XML jest otwarty standard, jest atrakcyjny wybór udostępnianie danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a6417-114">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="a6417-115">Podobnie protokołu SOAP jest otwarty standard, co pozwala na wybór atrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="a6417-115">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="a6417-116">[Serializacja kodu JSON](system-text-json-overview.md) wykonuje serializacji tylko właściwości publicznych i nie zachowuje wierności typów.</span><span class="sxs-lookup"><span data-stu-id="a6417-116">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="a6417-117">JSON to otwarty standard, który jest atrakcyjnym wyborem w przypadku udostępniania danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a6417-117">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="a6417-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="a6417-118">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="a6417-119">Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="a6417-119">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="a6417-120">Zawiera klasy, których można użyć do wykonywania serializacji obiektów w dokumentach formatu XML lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="a6417-120">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="a6417-121">Zawiera klasy, których można użyć do serializacji obiektów w dokumenty lub strumienie w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="a6417-121">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
