---
title: XML Document Object Model (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23be7e47dbe54d95eb29ef3b3cb169caeee3eff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579369"
---
# <a name="xml-document-object-model-dom"></a>XML Document Object Model (DOM)
Klasa XML modelu DOM (Document Object) ma reprezentacji w pamięci dokumentu XML. Modelu DOM umożliwia programowo odczytu, modyfikowania i modyfikowanie dokumentu XML. **XmlReader** klasy odczytuje również XML; jednak zapewnia dostęp niebuforowanym, tylko do przodu, tylko do odczytu. Oznacza to, że nie ma żadnych funkcji do edytowania wartości atrybutu lub zawartości elementu lub możliwość wstawiania i usuwania węzłów z **XmlReader**. Edytowanie jest podstawową funkcją modelu DOM. Jest typowe i sposób strukturalnych, że dane XML są reprezentowane w pamięci, mimo że rzeczywiste dane XML są przechowywane w sposób liniowy w pliku lub odbierane z innego obiektu. Poniżej przedstawiono dane XML.  
  
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
  
 Na poniższej ilustracji przedstawiono struktury pamięci podczas odczytywania te dane XML w strukturę modelu DOM.  
  
 ![Struktura dokumentu XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
Struktura dokumentu XML  
  
 W strukturze dokumentu XML każdy okrąg na tej ilustracji reprezentuje węzeł, która jest wywoływana **XmlNode** obiektu. **XmlNode** obiektu jest podstawowy obiekt w drzewie DOM. **XmlDocument** klasy, która rozszerza **XmlNode**, obsługuje metody do wykonywania operacji na dokumentu jako całość (na przykład załadowanie go do pamięci lub zapisywanie pliku XML w pliku. Ponadto **XmlDocument** umożliwia wyświetlanie i manipulowanie węzłów w całym dokumencie XML. Zarówno **XmlNode** i **XmlDocument** mają ulepszenia wydajności i użyteczności i metod i właściwości, aby:  
  
-   Węzły określone w modelu DOM, takie jak element węzły, węzły odwołanie do jednostki i tak dalej modyfikacji i dostępu.  
  
-   Pobierz całą węzłów, oprócz informacji znajdujących się w węźle, takich jak tekst w węźle elementu.  
  
    > [!NOTE]
    >  Jeśli aplikacja nie wymaga struktura lub edycji możliwości oferowane przez modelu DOM, **XmlReader** i **XmlWriter** klasy umożliwiają dostęp do strumienia niebuforowanym, tylko do przodu XML. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>.  
  
 **Węzeł** obiekty mają zestaw metod i właściwości, jak również właściwości podstawowych i dobrze zdefiniowany. Niektóre z tych właściwości są:  
  
-   Węzły mają węzła nadrzędnego pojedynczego, węzeł nadrzędny węzła bezpośrednio nad trwa. Tylko węzły, które nie ma rekordu nadrzędnego jest głównego dokumentu jest węzłem najwyższego poziomu i zawiera dokument i fragmenty dokumentu.  
  
-   Większość węzłów może mieć wiele węzłów podrzędnych, które są węzłami bezpośrednio pod nimi. Poniżej znajduje się lista typów węzłów, które mogą mieć węzłów podrzędnych.  
  
    -   **Dokument**  
  
    -   **DocumentFragment**  
  
    -   **Obiekt EntityReference**  
  
    -   **Element**  
  
    -   **Atrybut**  
  
     **XmlDeclaration**, **notacji**, **jednostki**, **CDATASection**, **tekst**,  **Komentarz**, **ProcessingInstruction**, i **DocumentType** węzły nie mają węzłów podrzędnych.  
  
-   Węzły, które są na tym samym poziomie reprezentowane na diagramie przez **książki** i **pubinfo** węzłów, są na tym samym poziomie.  
  
 Pojedynczy parametr modelu DOM jest sposób obsługi atrybutów. Atrybuty nie są węzłami, które są częścią nadrzędnej, podrzędne i relacje tego samego poziomu. Atrybuty są traktowane jako właściwość węzła elementu i są tworzone przez nazwę i pary wartości. Na przykład, jeśli masz składające się z danych XML `format="dollar`"skojarzone z elementem `price`, słowa `format` jest nazwa i wartość `format` atrybutu `dollar`. Aby pobrać `format="dollar"` atrybutu **cen** węzła, należy wywołać **GetAttribute** metody, gdy kursor znajduje się w `price` węzeł elementu. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów w modelu DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 XML jest w trybie odczytu do pamięci, węzły zostały utworzone. Niemniej jednak nie wszystkie węzły są tego samego typu. Element XML ma różne zasady i składni niż instrukcji przetwarzania. W związku z tym różnych danych jest w trybie odczytu, typ węzła jest przypisany do każdego węzła. Ten typ węzła Określa cechy i funkcje węzła.  
  
 Aby uzyskać więcej informacji na typy węzłów generowane w pamięci, zobacz [typy węzłów XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Aby uzyskać więcej informacji dotyczących obiektów utworzonych w węźle drzewa, zobacz [mapowania hierarchii obiektów do danych XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft ma rozszerzone interfejsów API, które są dostępne w sieci World Wide Web konsorcjum W3C DOM poziom 1 i poziom 2, aby ułatwić pracę z dokumentem XML. Podczas obsługi pełni ze standardami W3C, dodatkowych klas, metod i właściwości Dodaj funkcje oprócz co można zrobić za pomocą modelu DOM. W3C XML Nowe klasy umożliwiają dostęp do danych relacyjnych, umożliwiając metody synchronizowania danych ADO.NET, jednocześnie udostępnianie danych w formacie XML. Aby uzyskać więcej informacji, zobacz [synchronizowanie zestawu danych z dokumentu XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 Model DOM jest najbardziej przydatny w przypadku odczytywania danych XML do pamięci, aby zmienić jego struktury, aby dodać lub usunąć węzły lub zmodyfikować dane przechowywane przez węzeł jak tekst zawarty w elemencie. Jednak inne klasy są dostępne, które są szybsze niż w modelu DOM w innych scenariuszach. Dostęp do strumienia, szybka i niebuforowanym tylko do przodu do pliku XML, użyj **XmlReader** i **XmlWriter**. Jeśli potrzebujesz dostępie swobodnym z modelem kursor i **XPath**, użyj **Element XPathNavigator** klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy węzłów XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [Mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
