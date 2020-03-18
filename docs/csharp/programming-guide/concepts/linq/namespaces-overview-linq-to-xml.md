---
title: Przegląd przestrzeni nazw (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: d5f176a5561b77126ef23af996ab1e4bf51092ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868823"
---
# <a name="namespaces-overview-linq-to-xml"></a>Przegląd przestrzeni nazw (LINQ to XML)

W tym artykule przedstawiono <xref:System.Xml.Linq.XName> przestrzenie nazw, klasę i <xref:System.Xml.Linq.XNamespace> klasę.

## <a name="xml-names"></a>Nazwy XML

Nazwy XML są często źródłem złożoności w programowaniu XML. Nazwa XML składa się z obszaru nazw XML (nazywanego również identyfikatorem URI obszaru nazw XML) i nazwy lokalnej. Obszar nazw XML jest podobny do obszaru nazw w programie opartym na programie .NET Framework. Umożliwia unikatową kwalifikację nazw elementów i atrybutów. Pomaga to uniknąć konfliktów nazw między różnymi częściami dokumentu XML. Po zadeklarowaniu obszaru nazw XML można wybrać nazwę lokalną, która musi być unikatowa tylko w tym obszarze nazw.

Innym aspektem nazw XML są *prefiksy obszaru nazw*XML . Prefiksy XML powodują większość złożoności nazw XML. Te prefiksy umożliwiają utworzenie skrótu do obszaru nazw XML, co sprawia, że dokument XML jest bardziej zwięzły i zrozumiały. Jednak prefiksy XML zależą od ich kontekstu, aby mieć znaczenie, co zwiększa złożoność. Na przykład prefiks `aw` XML może być skojarzony z jednym obszarem nazw XML w jednej części drzewa XML i z innym obszarem nazw XML w innej części drzewa XML.

Jedną z zalet [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] używania z C# jest to, że nie trzeba używać prefiksów XML. Podczas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładowania lub analizowania dokumentu XML każdy prefiks XML jest rozpoznawany w odpowiednim obszarze nazw XML. Następnie podczas pracy z dokumentem, który używa przestrzeni nazw, prawie zawsze dostęp do obszarów nazw za pośrednictwem identyfikatora URI obszaru nazw, a nie za pośrednictwem prefiksu obszaru nazw. Gdy deweloperzy pracują z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nazwami XML w zawsze pracują z w pełni kwalifikowaną nazwą XML (czyli obszarem nazw XML i nazwą lokalną). Jednak w razie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] potrzeby umożliwia pracę z prefiksami obszaru nazw i sterowanie nim.

W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], klasa, która reprezentuje <xref:System.Xml.Linq.XName>nazwy XML jest . Nazwy XML są [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] często wyświetlane w całym interfejsie API, a wszędzie <xref:System.Xml.Linq.XName> tam, gdzie wymagana jest nazwa XML, znajdziesz parametr. Jednak rzadko pracujesz <xref:System.Xml.Linq.XName>bezpośrednio z . <xref:System.Xml.Linq.XName>zawiera niejawną konwersję z ciągu.

Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.
