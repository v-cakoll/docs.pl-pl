---
title: Przegląd przestrzeni nazw (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: d4c43a407921e1a74d1792f7cae4e320ca1234c0
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709896"
---
# <a name="namespaces-overview-linq-to-xml"></a>Przegląd przestrzeni nazw (LINQ to XML)

W <xref:System.Xml.Linq.XName> tym artykule wprowadzono przestrzenie nazw, klasy <xref:System.Xml.Linq.XNamespace> i klasy.
  
## <a name="xml-names"></a>Nazwy XML  

Nazwy XML często są źródłem złożoności w programowaniu XML. Nazwa XML składa się z przestrzeni nazw XML (nazywanej również identyfikatorem URI przestrzeni nazw XML) i nazwy lokalnej. Przestrzeń nazw XML jest podobna do przestrzeni nazw w programie opartym na .NET Framework. Umożliwia ona unikatową kwalifikowanie nazw elementów i atrybutów. Pozwala to uniknąć konfliktów nazw między różnymi częściami dokumentu XML. Po zadeklarowaniu przestrzeni nazw XML można wybrać lokalną nazwę, która musi być unikatowa w obrębie tej przestrzeni nazw.  
  
Innym aspektem nazw XML są *prefiksy przestrzeni nazw*XML. Prefiksy XML powodują większość złożoności nazw XML. Te prefiksy umożliwiają utworzenie skrótu dla przestrzeni nazw XML, co sprawia, że dokument XML jest bardziej zwięzły i zrozumiały. Jednak prefiksy XML są zależne od ich kontekstu, które mają znaczenie, co zwiększa złożoność. Na przykład prefiks `aw` XML może być skojarzony z jedną przestrzenią nazw XML w jednej części drzewa XML i z inną przestrzenią nazw XML w innej części drzewa XML.  
  
Jedną z zalet korzystania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z C# programu jest to, że nie trzeba używać prefiksów XML. Podczas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładowania lub analizowania dokumentu XML każdy prefiks XML jest rozpoznawany jako odpowiadający mu obszar nazw XML. Po wykonaniu tej czynności podczas pracy z dokumentem, który używa przestrzeni nazw, prawie zawsze uzyskuje się dostęp do przestrzeni nazw za pomocą identyfikatora URI przestrzeni nazw, a nie za pośrednictwem prefiksu przestrzeni nazw. Gdy deweloperzy pracują z nazwami [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML, zawsze pracują z w pełni kwalifikowaną nazwą XML (czyli przestrzenią nazw XML i nazwą lokalną). Jednak w razie potrzeby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia korzystanie z prefiksów przestrzeni nazw i kontrolowanie ich.  
  
W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programie Klasa, która reprezentuje nazwy XML, <xref:System.Xml.Linq.XName>to. Nazwy XML często [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pojawiają się w interfejsie API i wszędzie tam, gdzie jest wymagana nazwa XML, <xref:System.Xml.Linq.XName> parametr zostanie znaleziony. Jednak rzadko pracujemy bezpośrednio z <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName>zawiera niejawną konwersję z ciągu.  
  
Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.