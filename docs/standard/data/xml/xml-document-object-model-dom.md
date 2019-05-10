---
title: XML Document Object Model (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 664debd5432273cc25871f85d5d3c23f4c32dd6e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589841"
---
# <a name="xml-document-object-model-dom"></a>XML Document Object Model (DOM)
Klasa XML Document Object Model (DOM) jest reprezentacją w pamięci dokumentu XML. Model DOM umożliwia programowe do odczytu, modyfikowania i modyfikowanie dokumentu XML. **XmlReader** klasy odczytuje również XML; jednak zapewnia dostęp bez pamięci podręcznej, tylko do przodu, tylko do odczytu. Oznacza to, że nie ma możliwość edytowania wartości atrybutu lub zawartości elementu lub możliwość wstawiania i usuwania węzłów z **XmlReader**. Edytowanie jest podstawową funkcją DOM. To typowe i sposób strukturalnych, że dane XML są reprezentowane w pamięci, mimo, że rzeczywiste dane XML są przechowywane w sposób liniowy w przypadku pliku lub odbierane z innego obiektu. Poniżej znajduje się danych XML.  
  
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
  
 Poniższa ilustracja przedstawia struktury pamięci podczas odczytywania te dane XML do modelu DOM struktury.  
  
 ![Strukturę dokumentu XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
Strukturę dokumentu XML  
  
 W ramach strukturę dokumentu XML każdego okręgu na tej ilustracji reprezentuje węzeł, który nosi nazwę **XmlNode** obiektu. **XmlNode** obiekt jest obiektem podstawowe w drzewie DOM. **XmlDocument** klasy, która rozszerza **XmlNode**, obsługuje metody do wykonywania operacji na dokumencie jako całość (na przykład załadowanie go do pamięci lub zapisanie pliku XML w pliku. Ponadto **XmlDocument** umożliwia wyświetlanie i manipulowanie węzły w całym dokumencie XML. Zarówno **XmlNode** i **XmlDocument** mają ulepszenia wydajności i użyteczności, nie ma metody i właściwości, aby:  
  
- Dostępu i modyfikowania węzłów określone w modelu DOM, takich jak węzłów elementów, węzły odwołania jednostki i tak dalej.  
  
- Pobierz całą węzłów, oprócz informacji zawartych w węźle, takich jak tekst w węzeł elementu.  
  
    > [!NOTE]
    >  Jeśli aplikacja nie wymaga struktury lub edytowania możliwości oferowane przez modelu DOM, **XmlReader** i **XmlWriter** klasy zapewniają dostęp do strumienia bez pamięci podręcznej, tylko do przodu do pliku XML. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.  
  
 **Węzeł** obiekty mają zestaw metod i właściwości, jak również właściwości podstawowe i dobrze zdefiniowane. Niektóre z tych właściwości są następujące:  
  
- Węzły mają węzła nadrzędnego pojedynczego, węzeł nadrzędny jest węzłem bezpośrednio nad nimi. Tylko węzły, które nie mają elementu nadrzędnego jest katalog główny dokumentów, węzeł najwyższego poziomu, i zawiera sam dokument i fragmenty dokumentu.  
  
- Większość węzłów może mieć wiele węzły podrzędne, będące węzłami bezpośrednio poniżej. Oto lista typów węzłów, które mogą mieć węzłów podrzędnych.  
  
    - **Dokument**  
  
    - **DocumentFragment**  
  
    - **EntityReference**  
  
    - **Element**  
  
    - **Atrybut**  
  
     **XmlDeclaration**, **notacji**, **jednostki**, **CDATASection**, **tekstu**,  **Komentarz**, **ProcessingInstruction**, i **DocumentType** węzłów ma węzłów podrzędnych.  
  
- Węzły, które są na tym samym poziomie reprezentowane na diagramie przez **książki** i **pubinfo** węzły, są elementami równorzędnymi.  
  
 Pojedynczy parametr w modelu DOM jest jak obsługiwane atrybuty. Atrybuty nie są węzły, które są częścią nadrzędne, podrzędne i relacje element równorzędny. Atrybuty są traktowane jako właściwość węzła elementu i są tworzone przez nazwę i pary wartości. Na przykład, jeśli masz dane XML składający się z `format="dollar`"skojarzonego z elementem `price`, wyraz `format` to nazwa i wartość `format` atrybut jest `dollar`. Można pobrać `format="dollar"` atrybutu **cena** węzła, należy wywołać **GetAttribute** metody, gdy kursor znajduje się w `price` węzeł elementu. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów w modelu DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 Ponieważ XML jest do odczytu do pamięci, węzły zostały utworzone. Jednak nie wszystkie węzły są tego samego typu. Element w pliku XML ma różne reguły i składnia niż instrukcji przetwarzania. W związku z tym ponieważ różne dane zostaną odczytane, typ węzła jest przypisany do każdego węzła. Określa węzeł tego typu, cechy i funkcje węzła.  
  
 Aby uzyskać więcej informacji na temat typów węzłów generowane w pamięci, zobacz [typy węzłów XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Aby uzyskać więcej informacji na temat obiektów utworzonych w węźle drzewa, zobacz [mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft ma rozszerzone interfejsy API, które są dostępne w sieci World Wide Web Consortium (W3C) DOM poziom 1 i poziom 2 w celu ułatwienia pracy z dokumentu XML. Podczas pełnej obsłudze standardów W3C, dodatkowe klas, metod i właściwości Dodaj funkcje poza co można zrobić przy użyciu DOM XML W3C Nowe klasy zostanie umożliwiony dostęp do danych relacyjnych, zapewniając metody synchronizowania danych ADO.NET, jednocześnie udostępnianie danych w formacie XML. Aby uzyskać więcej informacji, zobacz [synchronizowanie elementu DataSet z elementem XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 Model DOM jest najbardziej przydatne do odczytywania danych XML do pamięci, aby zmienić jego struktury, aby dodawać lub usuwać węzły lub zmodyfikować dane przechowywane przez węzeł jak tekst zawarty w elemencie. Jednak inne klasy są dostępne, które są szybsze niż DOM w innych scenariuszach. Aby uzyskać dostęp do strumienia, szybka i niebuforowanym tylko do przodu do pliku XML, należy użyć **XmlReader** i **XmlWriter**. Jeśli potrzebujesz dostępu losowego, za pomocą modelu kursora i **XPath**, użyj **klasy XPathNavigator** klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Typy węzłów XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)
- [Mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
