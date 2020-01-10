---
title: XML Document Object Model (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
ms.openlocfilehash: 4faa481a6331863112b7dba65bdbccb69cd12b7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709962"
---
# <a name="xml-document-object-model-dom"></a>XML Document Object Model (DOM)

Klasa XML Document Object Model (DOM) to reprezentacja dokumentu XML w pamięci. DOM pozwala programistycznie odczytywać, manipulować i modyfikować dokument XML. Klasa **XmlReader** odczytuje również kod XML; jednak zapewnia dostęp tylko do odczytu w trybie niebuforowanym. Oznacza to, że nie ma możliwości edytowania wartości atrybutu lub zawartości elementu albo możliwość wstawiania i usuwania węzłów z elementem **XmlReader**. Edytowanie jest podstawową funkcją modelu DOM. Jest to typowy i strukturalny sposób, w jaki dane XML są reprezentowane w pamięci, chociaż rzeczywiste dane XML są przechowywane w sposób liniowy, gdy plik lub pochodzą z innego obiektu. Poniżej przedstawiono dane XML.

## <a name="input"></a>Dane wejściowe

```xml
<?xml version="1.0"?>
  <books>
    <book>
        <author>Carson</author>
        <price format="dollar">31.95</price>
        <pubdate>05/01/2001</pubdate>
    </book>
    <pubinfo>
        <publisher>MSPress</publisher>
        <state>WA</state>
    </pubinfo>
  </books>
```

Na poniższej ilustracji przedstawiono sposób, w jaki pamięć jest strukturalna, gdy dane XML są odczytywane w strukturze modelu DOM.

![Struktura dokumentu XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree") Struktura dokumentu XML

W strukturze dokumentu XML każdy okrąg na tej ilustracji reprezentuje węzeł, który jest nazywany obiektem **XmlNode** . Obiekt **XmlNode** jest obiektem podstawowym w drzewie dom. Klasa **XmlDocument** , która rozszerza element **XmlNode**, obsługuje metody wykonywania operacji na dokumencie jako całość (na przykład ładując go do pamięci lub zapisując plik XML do pliku. Ponadto Metoda **XmlDocument** umożliwia wyświetlanie węzłów w całym dokumencie XML i manipulowanie nimi. Zarówno element **XmlNode** , jak i **XmlDocument** mają udoskonalenia wydajności i użyteczności oraz mają metody i właściwości, aby:

- Dostęp i modyfikowanie węzłów specyficznych dla modelu DOM, takich jak węzły elementów, węzły odwołań jednostek i tak dalej.

- Pobierz wszystkie węzły, oprócz informacji zawartych w węźle, takich jak tekst w węźle elementu.

  > [!NOTE]
  > Jeśli aplikacja nie wymaga struktury ani możliwości edytowania dostarczonych przez model DOM, klasy **XmlReader** i **XmlWriter** zapewniają dostęp do strumienia XML w niebuforowanej postaci tylko do przodu. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.

Obiekty **węzłów** mają zestaw metod i właściwości, a także podstawowe i dobrze zdefiniowane cechy. Niektóre z tych cech są następujące:

- Węzły mają jeden węzeł nadrzędny, czyli węzeł nadrzędny, który znajduje się bezpośrednio nad nimi. Jedynymi węzłami, które nie mają elementu nadrzędnego, jest katalog główny dokumentu, ponieważ jest to węzeł najwyższego poziomu i zawiera sam dokument i fragmenty dokumentu.

- Większość węzłów może mieć wiele węzłów podrzędnych, które są węzłami bezpośrednio poniżej. Poniżej znajduje się lista typów węzłów, które mogą mieć węzły podrzędne.

  - **Document**

  - **DocumentFragment**

  - **EntityReference**

  - **Element**

  - **Atrybut**

  Węzły **xmldeklaracji**, **Notation**, **Entity**, **CDATASection**, **Text**, **Comment**, **ProcessingInstruction**i **DocumentType** nie mają węzłów podrzędnych.

- Węzły, które znajdują się na tym samym poziomie, reprezentowane na diagramie przez węzły **książka** i **pubinfo** , są równorzędne.

Jedną z cech modelu DOM jest sposób obsługi atrybutów. Atrybuty nie są węzłami, które są częścią relacji nadrzędnej, podrzędnej i równorzędnej. Atrybuty są uważane za właściwość węzła elementu i składają się z nazwy i pary wartości. Na przykład jeśli masz dane XML zawierające `format="dollar`"skojarzone z elementem `price`, słowo `format` jest nazwą, a wartość atrybutu `format` jest `dollar`. Aby pobrać atrybut `format="dollar"` węzła **Cena** , należy wywołać metodę **GetAttribute** , gdy kursor znajduje się w węźle elementu `price`. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów w modelu dom](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).

Ponieważ kod XML jest odczytywany w pamięci, tworzone są węzły. Jednak nie wszystkie węzły są tego samego typu. Element w kodzie XML ma różne reguły i składnię niż instrukcja przetwarzania. W związku z tym, jako że odczytywane są różne dane, do każdego węzła jest przypisany typ węzła. Ten typ węzła określa cechy i funkcje węzła.

Aby uzyskać więcej informacji na temat typów węzłów generowanych w pamięci, zobacz [typy węzłów XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Aby uzyskać więcej informacji na temat obiektów utworzonych w drzewie węzłów, zobacz [Mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).

Firma Microsoft rozszerzyła interfejsy API, które są dostępne w organizacja World Wide Web Consortium (W3C) DOM Level 1 i 2, aby ułatwić pracę z dokumentem XML. W pełni obsługujące standardy W3C, dodatkowe klasy, metody i właściwości dodają funkcje wykraczające poza to, co można zrobić za pomocą W3C XML DOM. Nowe klasy umożliwiają dostęp do danych relacyjnych, dając metody synchronizowania z danymi ADO.NET, jednocześnie udostępniając dane w formacie XML. Aby uzyskać więcej informacji, zobacz [synchronizowanie zestawu danych z XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).

DOM jest najbardziej przydatny do odczytywania danych XML w pamięci, aby zmienić jej strukturę, dodać lub usunąć węzły lub zmodyfikować dane przechowywane przez węzeł tak jak w tekście zawartym w elemencie. Jednak inne klasy są dostępne szybciej niż DOM w innych scenariuszach. Aby uzyskać szybki, niebuforowany dostęp do strumienia XML tylko do przodu, użyj elementu **XmlReader** i **XmlWriter**. Jeśli potrzebujesz dostępu losowego z modelem kursorów i **XPath**, użyj klasy **XPathNavigator** .

## <a name="see-also"></a>Zobacz także

- [Typy węzłów XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)
- [Mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
