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
# <a name="xml-and-soap-serialization"></a>Serializacja XML i SOAP

Serializacji XML konwertuje (deserializacji) publiczne pola i właściwości obiektu oraz parametry i zwracane wartości metod do strumienia XML, który jest zgodny z konkretnym dokumentem języka definicji schematu XML (XSD). Powoduje serializacji XML w silnie typizowanej klasy z właściwości publiczne i pola, które są konwertowane na format seryjny (w tym przypadku XML) do przechowywania lub transportu.

Ponieważ kod XML jest otwarty standard, strumień XML może być przetwarzany przez dowolną aplikację, w razie konieczności, niezależnie od platformy. Na przykład usługi sieci Web XML utworzone za pomocą ASP.NET używają <xref:System.Xml.Serialization.XmlSerializer> klasy do tworzenia strumieni XML, które przesyłają dane między aplikacjami usługi sieci Web XML w Internecie lub w intranecie. Z kolei deserializacji pobiera strumień XML i rekonstruuje obiektu.

Umożliwia także serializacji XML można serializować obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP. Protokołu SOAP to protokół oparte na języku XML, zaprojektowany specjalnie w celu transportu wywołań procedur za pomocą języka XML.

Do serializacji lub deserializacji obiekty, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby utworzyć klasy serializacji, należy użyć narzędzia definicji schematu XML.

## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
- [Usługi sieci Web XML utworzone za pomocą ASP.NET i klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
