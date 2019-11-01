---
title: Informacje dotyczące LINQ to XML właściwości dynamicznych
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 48b51e92eb78786b2cc189e3e7daa00875b41585
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197052"
---
# <a name="linq-to-xml-dynamic-properties"></a>Właściwości dynamiczne LINQ to XML

Ta sekcja zawiera informacje referencyjne na temat właściwości dynamicznych w LINQ to XML. W szczególnych przypadkach te właściwości są uwidaczniane przez klasy <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które znajdują się w przestrzeni nazw <xref:System.Xml.Linq>.

Jak wyjaśniono w temacie [Omówienie powiązania danych WPF z LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md), Każda właściwość dynamiczna jest równoważna z standardową właściwością publiczną lub metodą w tej samej klasie. Tych standardowych członków należy używać w większości celów; właściwości dynamiczne są udostępniane w ramach scenariuszy powiązań danych LINQ to XML. Aby uzyskać więcej informacji na temat standardowych elementów członkowskich tych klas, zobacz tematy dotyczące <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>.

W odniesieniu do ich rozwiązanych wartości właściwości dynamiczne w tej sekcji należą do dwóch kategorii:

- Proste, takie jak `Value` właściwości w klasach <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które rozpoznają się z jedną wartością.

- Indeksowane wartości, takie jak [elementy](elements-xelement-dynamic-property.md) i właściwości [potomne](descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement>, które są rozpoznawane jako typ indeksatora. Aby można było rozpoznać typy indeksatora do żądanej wartości lub kolekcji, należy do nich przekazywać parametry rozszerzonej nazwy.

Wszystkie właściwości dynamiczne zwracające wartość indeksowaną typu <xref:System.Collections.Generic.IEnumerable%601> korzystają z odroczonego wykonania. Aby uzyskać więcej informacji o odroczonym wykonywaniu, zobacz [wprowadzenie do zapytań LINQC#()](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="reference"></a>Tematy pomocy

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Powiązanie danych WPF z LINQ to XML przegląd](wpf-data-binding-with-linq-to-xml-overview.md)
- [Wprowadzenie do zapytań LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
