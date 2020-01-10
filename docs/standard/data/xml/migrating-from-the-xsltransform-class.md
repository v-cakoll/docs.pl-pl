---
title: Migrowanie z klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 95e71e1fdd0ded145025316a5d6597b27a6cc970
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710651"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrowanie z klasy XslTransform

Architektura XSLT została przeprojektowana w wersji programu Visual Studio 2005. Klasa <xref:System.Xml.Xsl.XslTransform> została zastąpiona przez klasę <xref:System.Xml.Xsl.XslCompiledTransform>.

W poniższych sekcjach opisano niektóre główne różnice między <xref:System.Xml.Xsl.XslCompiledTransform> i klasami <xref:System.Xml.Xsl.XslTransform>.

## <a name="performance"></a>Wydajność

Klasa <xref:System.Xml.Xsl.XslCompiledTransform> obejmuje wiele ulepszeń wydajności. Nowy procesor XSLT kompiluje arkusz stylów XSLT w dół do wspólnego formatu pośredniego, podobnie jak środowisko uruchomieniowe języka wspólnego (CLR) dla innych języków programowania. Po skompilowaniu arkusza stylów można go buforować i ponownie używać.

Klasa <xref:System.Xml.Xsl.XslCompiledTransform> obejmuje również inne optymalizacje, które znacznie przyspieszają od klasy <xref:System.Xml.Xsl.XslTransform>.

> [!NOTE]
> Chociaż ogólna wydajność klasy <xref:System.Xml.Xsl.XslCompiledTransform> jest lepsza niż Klasa <xref:System.Xml.Xsl.XslTransform>, Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> klasy <xref:System.Xml.Xsl.XslCompiledTransform> może działać wolniej niż Metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> klasy <xref:System.Xml.Xsl.XslTransform> przy pierwszym wywołaniu dla transformacji. Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)

## <a name="security"></a>Zabezpieczenia

Domyślnie Klasa <xref:System.Xml.Xsl.XslCompiledTransform> wyłącza obsługę funkcji `document()` XSLT i skryptów osadzonych. Te funkcje można włączyć przez utworzenie obiektu <xref:System.Xml.Xsl.XsltSettings>, w którym włączono funkcje i przekazanie go do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>. Poniższy przykład pokazuje, jak włączyć obsługę skryptów i przeprowadzić transformację XSLT.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).

## <a name="new-features"></a>Nowe funkcje

### <a name="temporary-files"></a>Pliki tymczasowe

Pliki tymczasowe są czasami generowane podczas przetwarzania XSLT. Jeśli arkusz stylów zawiera bloki skryptów lub jeśli zostanie skompilowany z ustawieniem Debuguj ustawionym na true, pliki tymczasowe można utworzyć w folderze% TEMP%. Mogą występować wystąpienia, gdy niektóre pliki tymczasowe nie zostaną usunięte ze względu na problemy z chronometrażem. Na przykład jeśli pliki są używane przez bieżącą domenę aplikacji lub przez debuger, finalizator obiektu <xref:System.CodeDom.Compiler.TempFileCollection> nie będzie mógł go usunąć.

Właściwość <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> może służyć do dodatkowego oczyszczania, aby upewnić się, że wszystkie pliki tymczasowe są usuwane z klienta programu.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Obsługa elementu xsl: Output i XmlWriter

Klasa <xref:System.Xml.Xsl.XslTransform> została zignorowana `xsl:output` ustawień, gdy dane wyjściowe transformacji zostały wysłane do obiektu <xref:System.Xml.XmlWriter>. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> ma właściwość <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A>, która zwraca obiekt <xref:System.Xml.XmlWriterSettings> zawierający informacje wyjściowe pochodzące z elementu `xsl:output` arkusza stylów. Obiekt <xref:System.Xml.XmlWriterSettings> służy do tworzenia obiektu <xref:System.Xml.XmlWriter> z prawidłowymi ustawieniami, które mogą być przesyłane do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Poniższy C# kod ilustruje to zachowanie:

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a>Opcja debugowania

Klasa <xref:System.Xml.Xsl.XslCompiledTransform> może generować informacje debugowania, które umożliwiają debugowanie arkusza stylów za pomocą debugera Microsoft Visual Studio. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.

## <a name="behavioral-differences"></a>Różnice w zachowaniu

### <a name="transforming-to-an-xmlreader"></a>Przekształcanie do elementu XmlReader

Klasa <xref:System.Xml.Xsl.XslTransform> ma kilka przeciążenia transformacji, które zwracają wyniki transformacji jako obiekt <xref:System.Xml.XmlReader>. Te przeciążenia mogą służyć do załadowania wyników transformacji do reprezentacji w pamięci (takiej jak <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument>) bez naliczania obciążeń związanych z serializacji i deserializacji wynikowego drzewa XML. Poniższy C# kod ilustruje sposób ładowania wyników transformacji do obiektu <xref:System.Xml.XmlDocument>.

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

Klasa <xref:System.Xml.Xsl.XslCompiledTransform> nie obsługuje transformacji do obiektu <xref:System.Xml.XmlReader>. Można jednak wykonać coś podobnego przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A>, aby załadować utworzone drzewo XML bezpośrednio z <xref:System.Xml.XmlWriter>. Poniższy C# kod pokazuje, jak wykonać to samo zadanie przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform>.

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a>Zachowanie uznaniowe

Zalecenie dotyczące formatu W3C XSL Transformations (XSLT) w wersji 1,0 zawiera obszary, w których dostawca implementacji może zdecydować, jak obsługiwać sytuację. Te obszary są uważane za zachowanie uznaniowe. Istnieje kilka obszarów, w których <xref:System.Xml.Xsl.XslCompiledTransform> działa inaczej niż Klasa <xref:System.Xml.Xsl.XslTransform>. Aby uzyskać więcej informacji, zobacz [odzyskanie błędów XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).

### <a name="extension-objects-and-script-functions"></a>Obiekty rozszerzeń i funkcje skryptów

w <xref:System.Xml.Xsl.XslCompiledTransform> wprowadzono dwa nowe ograniczenia dotyczące używania funkcji skryptów:

- Tylko metody publiczne mogą być wywoływane z wyrażeń XPath.

- Przeciążenia są odróżniane od siebie w zależności od liczby argumentów. Jeśli więcej niż jedno Przeciążenie ma taką samą liczbę argumentów, zostanie zgłoszony wyjątek.

W <xref:System.Xml.Xsl.XslCompiledTransform>powiązanie (wyszukiwanie nazw metod) z funkcjami skryptu występuje w czasie kompilacji, a arkusze stylów, które działały z XslTransform, mogą spowodować wyjątek podczas ładowania z <xref:System.Xml.Xsl.XslCompiledTransform>.

<xref:System.Xml.Xsl.XslCompiledTransform> obsługuje `msxsl:using` i `msxsl:assembly` elementów podrzędnych w elemencie `msxsl:script`. Elementy `msxsl:using` i `msxsl:assembly` są używane do deklarowania dodatkowych przestrzeni nazw i zestawów do użycia w bloku skryptu. Aby uzyskać więcej informacji, zobacz [bloki skryptów przy użyciu msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .

<xref:System.Xml.Xsl.XslCompiledTransform> zabrania obiektów rozszerzeń, które mają wiele przeciążeń z tą samą liczbą argumentów.

### <a name="msxml-functions"></a>Funkcje programu MSXML

Dodano obsługę dodatkowych funkcji MSXML do klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Na poniższej liście opisano nowe lub udoskonalone funkcje:

- msxsl: zestaw węzłów: <xref:System.Xml.Xsl.XslTransform> wymaga argumentu funkcji [funkcji zestawu węzłów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) jako fragmentu drzewa wyników. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> nie ma tego wymagania.

- msxsl: Version: Ta funkcja jest obsługiwana w <xref:System.Xml.Xsl.XslCompiledTransform>.

- Funkcje rozszerzenia XPath: [Funkcja MS: Compare — porównanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC funkcja](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: Namespace-URI](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: funkcja local-name](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), funkcja [MS: format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))i MS: funkcje [funkcji Time w formacie godziny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) są teraz obsługiwane.

- Funkcje rozszerzenia XPath powiązane ze schematem: funkcje te nie są obsługiwane natywnie przez <xref:System.Xml.Xsl.XslCompiledTransform>. Można je jednak zaimplementować jako funkcje rozszerzenia.

## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
