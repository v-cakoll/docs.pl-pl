---
title: Serializacja XML i SOAP
description: Ten przegląd omawia serializację XML, który może służyć do serializacji obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 6b7d6f59694a28207758fa7772781eed073917e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379543"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="5b018-103">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="5b018-103">XML and SOAP serialization</span></span>

<span data-ttu-id="5b018-104">Serializacji XML konwertuje (deserializacji) publiczne pola i właściwości obiektu oraz parametry i zwracane wartości metod do strumienia XML, który jest zgodny z konkretnym dokumentem języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="5b018-104">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="5b018-105">Powoduje serializacji XML w silnie typizowanej klasy z właściwości publiczne i pola, które są konwertowane na format seryjny (w tym przypadku XML) do przechowywania lub transportu.</span><span class="sxs-lookup"><span data-stu-id="5b018-105">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="5b018-106">Ponieważ kod XML jest otwarty standard, strumień XML może być przetwarzany przez dowolną aplikację, w razie konieczności, niezależnie od platformy.</span><span class="sxs-lookup"><span data-stu-id="5b018-106">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="5b018-107">Na przykład usługi sieci Web XML utworzone za pomocą ASP.NET używają <xref:System.Xml.Serialization.XmlSerializer> klasy do tworzenia strumieni XML, które przesyłają dane między aplikacjami usługi sieci Web XML w Internecie lub w intranecie.</span><span class="sxs-lookup"><span data-stu-id="5b018-107">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="5b018-108">Z kolei deserializacji pobiera strumień XML i rekonstruuje obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b018-108">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="5b018-109">Umożliwia także serializacji XML można serializować obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5b018-109">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="5b018-110">Protokołu SOAP to protokół oparte na języku XML, zaprojektowany specjalnie w celu transportu wywołań procedur za pomocą języka XML.</span><span class="sxs-lookup"><span data-stu-id="5b018-110">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="5b018-111">Do serializacji lub deserializacji obiekty, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy.</span><span class="sxs-lookup"><span data-stu-id="5b018-111">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="5b018-112">Aby utworzyć klasy serializacji, należy użyć narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="5b018-112">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b018-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b018-113">See also</span></span>

- [<span data-ttu-id="5b018-114">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="5b018-114">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="5b018-115">[Usługi sieci Web XML utworzone za pomocą ASP.NET i klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5b018-115">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
