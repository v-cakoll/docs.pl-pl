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
# <a name="serialization-in-net"></a>Serializacja w .NET
Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane. Uzupełnienia do serializacji jest deserializacji, który konwertuje strumienia na obiekt. Razem te procesy umożliwiają danych można łatwo przechowywane i przekazywane.  
  
.NET oferuje dwa serializacji technologii:  
  
- Serializacja binarna zachowuje wierności typu, co ułatwia zachowania stanu obiektu między wywołań różnych aplikacji. Na przykład można udostępniać obiektu między różnymi aplikacjami, szeregując go do Schowka. Można serializować obiektu w strumieniu na dysku w pamięci, za pośrednictwem sieci i tak dalej. Zdalne używa serializacji do przekazania obiektów "przez wartość" z jednej domeny komputera lub aplikacji do innego.  
  
- Serializacji XML serializuje tylko właściwości publiczne i pola i nie zostaną zachowane wierności typu. Jest to przydatne, jeśli chcesz podać lub zużywać danych nie ograniczając aplikacji, która używa tych danych. Ponieważ kod XML jest otwarty standard, jest atrakcyjny wybór udostępnianie danych w sieci Web. Podobnie protokołu SOAP jest otwarty standard, co pozwala na wybór atrakcyjny.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Serializacja — instrukcje](../../../docs/standard/serialization/serialization-how-to-topics.md)  
Zawiera także łącza do tematów instrukcje zawarte w tej sekcji.
  
[Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.

[Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.

[Narzędzia do serializacji](../../../docs/standard/serialization/serialization-tools.md)  
Te narzędzia ułatwiają tworzenie kodu serializacji.

[Przykłady serializacji](../../../docs/standard/serialization/serialization-samples.md)  
Przykłady pokazują, jak to zrobić serializacji.

## <a name="reference"></a>Tematy pomocy
<xref:System.Runtime.Serialization> Zawiera klasy, które mogą służyć do serializacji i deserializacji obiektów.
  
<xref:System.Xml.Serialization>  
Zawiera klasy, których można użyć do wykonywania serializacji obiektów w dokumentach formatu XML lub strumieni.
