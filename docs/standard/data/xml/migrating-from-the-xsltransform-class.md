---
title: Migrowanie z klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 8383d8cb3e5819c46a0716c59323e492bb9add8e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937992"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrowanie z klasy XslTransform

Architektura XSLT została przeprojektowana w wersji programu Visual Studio 2005. <xref:System.Xml.Xsl.XslTransform> Klasa została zastąpiona przez <xref:System.Xml.Xsl.XslCompiledTransform> klasę.

W poniższych sekcjach opisano niektóre główne różnice między <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> klasami i.

## <a name="performance"></a>Wydajność

<xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera wiele ulepszeń wydajności. Nowy procesor XSLT kompiluje arkusz stylów XSLT w dół do wspólnego formatu pośredniego, podobnie jak środowisko uruchomieniowe języka wspólnego (CLR) dla innych języków programowania. Po skompilowaniu arkusza stylów można go buforować i ponownie używać.

<xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera również inne optymalizacje, które znacznie przyspieszają od <xref:System.Xml.Xsl.XslTransform> klasy.

> [!NOTE]
> Chociaż <xref:System.Xml.Xsl.XslCompiledTransform> ogólna wydajność klasy jest lepsza niż <xref:System.Xml.Xsl.XslTransform> Klasa, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslCompiledTransform> klasy może działać wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> klasy, gdy jest wywoływana po raz pierwszy. Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)

## <a name="security"></a>Zabezpieczenia

Domyślnie <xref:System.Xml.Xsl.XslCompiledTransform> Klasa wyłącza obsługę funkcji XSLT `document()` i skryptów osadzonych. Te funkcje można włączyć, tworząc <xref:System.Xml.Xsl.XsltSettings> obiekt z włączonymi funkcjami i przekazując go do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Poniższy przykład pokazuje, jak włączyć obsługę skryptów i przeprowadzić transformację XSLT.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).

## <a name="new-features"></a>Nowe funkcje

### <a name="temporary-files"></a>Pliki tymczasowe

Pliki tymczasowe są czasami generowane podczas przetwarzania XSLT. Jeśli arkusz stylów zawiera bloki skryptów lub jeśli zostanie skompilowany z ustawieniem Debuguj ustawionym na true, pliki tymczasowe można utworzyć w folderze% TEMP%. Mogą występować wystąpienia, gdy niektóre pliki tymczasowe nie zostaną usunięte ze względu na problemy z chronometrażem. Na przykład jeśli pliki są używane przez bieżącą domenę aplikacji lub przez debuger, finalizator <xref:System.CodeDom.Compiler.TempFileCollection> obiektu nie będzie mógł go usunąć.

<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Właściwość może służyć do dodatkowego oczyszczania, aby upewnić się, że wszystkie pliki tymczasowe są usuwane z klienta programu.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Obsługa elementu xsl: Output i XmlWriter

<xref:System.Xml.Xsl.XslTransform> Klasa zignorował `xsl:output` ustawienia, gdy dane wyjściowe transformacji zostały wysłane do <xref:System.Xml.XmlWriter> obiektu. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> ma właściwość, która zwraca <xref:System.Xml.XmlWriterSettings> obiekt zawierający informacje wyjściowe pochodzące z `xsl:output` elementu arkusza stylów. <xref:System.Xml.XmlWriterSettings> Obiekt jest używany do tworzenia <xref:System.Xml.XmlWriter> obiektu z prawidłowymi ustawieniami, które mogą być przesyłane do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Poniższy kod w języku C# ilustruje to zachowanie:

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

<xref:System.Xml.Xsl.XslCompiledTransform> Klasa może generować informacje debugowania, które umożliwiają debugowanie arkusza stylów za pomocą debugera Microsoft Visual Studio. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.

## <a name="behavioral-differences"></a>Różnice w zachowaniu

### <a name="transforming-to-an-xmlreader"></a>Przekształcanie do elementu XmlReader

<xref:System.Xml.Xsl.XslTransform> Klasa ma kilka przeciążenia transformacji, które zwracają wyniki transformacji jako <xref:System.Xml.XmlReader> obiekt. Te przeciążenia mogą służyć do załadowania wyników transformacji do reprezentacji w pamięci (takiej jak <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument>) bez naliczania obciążeń związanych z serializacji i deserializacji wynikowego drzewa XML. Poniższy kod w języku C# pokazuje, jak załadować wyniki transformacji do <xref:System.Xml.XmlDocument> obiektu.

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie obsługuje transformacji do <xref:System.Xml.XmlReader> obiektu. Można jednak wykonać coś podobnego przy użyciu <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metody do załadowania utworzonego drzewa XML bezpośrednio z obiektu. <xref:System.Xml.XmlWriter> Poniższy kod w języku C# pokazuje, jak wykonać to samo zadanie <xref:System.Xml.Xsl.XslCompiledTransform>przy użyciu polecenia.

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a>Zachowanie uznaniowe

Zalecenie dotyczące formatu W3C XSL Transformations (XSLT) w wersji 1,0 zawiera obszary, w których dostawca implementacji może zdecydować, jak obsługiwać sytuację. Te obszary są uważane za zachowanie uznaniowe. Istnieje kilka obszarów, w <xref:System.Xml.Xsl.XslCompiledTransform> których zachowanie różni się od <xref:System.Xml.Xsl.XslTransform> klasy. Aby uzyskać więcej informacji, zobacz [odzyskanie błędów XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).

### <a name="extension-objects-and-script-functions"></a>Obiekty rozszerzeń i funkcje skryptów

<xref:System.Xml.Xsl.XslCompiledTransform>wprowadza dwa nowe ograniczenia dotyczące używania funkcji skryptów:

- Tylko metody publiczne mogą być wywoływane z wyrażeń XPath.

- Przeciążenia są odróżniane od siebie w zależności od liczby argumentów. Jeśli więcej niż jedno Przeciążenie ma taką samą liczbę argumentów, zostanie zgłoszony wyjątek.

W <xref:System.Xml.Xsl.XslCompiledTransform>programie powiązanie (wyszukiwanie nazw metod) z funkcjami skryptu występuje w czasie kompilacji, a arkusze stylów, które działały z XslTransform, mogą spowodować wyjątek podczas ładowania z <xref:System.Xml.Xsl.XslCompiledTransform>.

<xref:System.Xml.Xsl.XslCompiledTransform>obsługuje elementy `msxsl:using` mające i `msxsl:assembly` elementów podrzędnych `msxsl:script` w obrębie elementu. Elementy `msxsl:using` i `msxsl:assembly` są używane do deklarowania dodatkowych przestrzeni nazw i zestawów do użycia w bloku skryptu. Aby uzyskać więcej informacji, zobacz [bloki skryptów przy użyciu msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .

<xref:System.Xml.Xsl.XslCompiledTransform>zabrania obiektów rozszerzeń, które mają wiele przeciążeń z tą samą liczbą argumentów.

### <a name="msxml-functions"></a>Funkcje programu MSXML

Do <xref:System.Xml.Xsl.XslCompiledTransform> klasy dodano obsługę dodatkowych funkcji MSXML. Na poniższej liście opisano nowe lub udoskonalone funkcje:

- msxsl: zestaw węzłów: <xref:System.Xml.Xsl.XslTransform> wymagany argument funkcji [funkcji zestawu węzłów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) musi być fragmentem drzewa wynikowego. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie ma tego wymagania.

- msxsl: wersja: Ta funkcja jest obsługiwana w <xref:System.Xml.Xsl.XslCompiledTransform>programie.

- Funkcje rozszerzenia XPath: [Funkcja MS: Compare — porównanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC funkcja](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: Namespace-URI](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: funkcja local-name](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), funkcja [MS: format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))i MS: funkcje [funkcji Time w formacie godziny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) są teraz obsługiwane.

- Funkcje rozszerzenia XPath powiązane ze schematem: funkcje te nie są obsługiwane natywnie <xref:System.Xml.Xsl.XslCompiledTransform>przez program. Można je jednak zaimplementować jako funkcje rozszerzenia.

## <a name="see-also"></a>Zobacz też

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
