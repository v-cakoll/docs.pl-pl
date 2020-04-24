---
title: Serializacja — .NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053347"
---
# <a name="serialization-in-net"></a><span data-ttu-id="73f54-102">Serializacja w .NET</span><span class="sxs-lookup"><span data-stu-id="73f54-102">Serialization in .NET</span></span>

<span data-ttu-id="73f54-103">Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane.</span><span class="sxs-lookup"><span data-stu-id="73f54-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="73f54-104">Uzupełnienie serializacji jest deserializacji, która konwertuje strumień na obiekt.</span><span class="sxs-lookup"><span data-stu-id="73f54-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="73f54-105">Procesy te umożliwiają jednoczesne przechowywanie i przesyłanie danych.</span><span class="sxs-lookup"><span data-stu-id="73f54-105">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="73f54-106">Platforma .NET oferuje następujące technologie serializacji:</span><span class="sxs-lookup"><span data-stu-id="73f54-106">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="73f54-107">[Serializacja binarna](binary-serialization.md) zachowuje wierność typu, co jest przydatne do zachowania stanu obiektu między różnymi wywołaniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73f54-107">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="73f54-108">Na przykład można udostępnić obiekt między różnymi aplikacjami, serializacji go do Schowka.</span><span class="sxs-lookup"><span data-stu-id="73f54-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="73f54-109">Można serializować obiektu w strumieniu na dysku w pamięci, za pośrednictwem sieci i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="73f54-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="73f54-110">Komunikacja zdalna używa serializacji do przekazywania obiektów "według wartości" z jednego komputera lub domeny aplikacji do innej.</span><span class="sxs-lookup"><span data-stu-id="73f54-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="73f54-111">[Serializacji XML i SOAP](xml-and-soap-serialization.md) serializować tylko właściwości publiczne i pola i nie zachowuje wierności typów.</span><span class="sxs-lookup"><span data-stu-id="73f54-111">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="73f54-112">Jest to przydatne, gdy chcesz zapewnić lub wykorzystać dane bez ograniczania aplikacji, która korzysta z danych.</span><span class="sxs-lookup"><span data-stu-id="73f54-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="73f54-113">Ponieważ kod XML jest otwarty standard, jest atrakcyjny wybór udostępnianie danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="73f54-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="73f54-114">Podobnie protokołu SOAP jest otwarty standard, co pozwala na wybór atrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="73f54-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="73f54-115">[Serializacja kodu JSON](system-text-json-overview.md) wykonuje serializacji tylko właściwości publicznych i nie zachowuje wierności typów.</span><span class="sxs-lookup"><span data-stu-id="73f54-115">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="73f54-116">JSON to otwarty standard, który jest atrakcyjnym wyborem w przypadku udostępniania danych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="73f54-116">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="73f54-117">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="73f54-117">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="73f54-118">Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.</span><span class="sxs-lookup"><span data-stu-id="73f54-118">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="73f54-119">Zawiera klasy, których można użyć do wykonywania serializacji obiektów w dokumentach formatu XML lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="73f54-119">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="73f54-120">Zawiera klasy, których można użyć do serializacji obiektów w dokumenty lub strumienie w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="73f54-120">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
