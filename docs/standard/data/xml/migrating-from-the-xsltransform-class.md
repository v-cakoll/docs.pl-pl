---
title: Migrowanie z klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8b8c21af8ca0a21d97e8246ad82c42aaaf4974
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678577"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrowanie z klasy XslTransform
Architektura XSLT został przeprojektowany w [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] wydania. <xref:System.Xml.Xsl.XslTransform> Klasy został zastąpiony przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 W poniższych sekcjach opisano niektóre główne różnice między <xref:System.Xml.Xsl.XslCompiledTransform> i <xref:System.Xml.Xsl.XslTransform> klasy.  
  
## <a name="performance"></a>Wydajność  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera wiele ulepszeń wydajności. Nowe procesora XSLT kompiluje arkusza stylów XSLT w dół do typowego formatu pośredniego, podobnie jak w przypadku innych języków programowania działania środowisko uruchomieniowe języka wspólnego (CLR). Po skompilowaniu arkusz stylów może pamięci podręcznej i ponownie używane.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasy zawiera również inne optymalizacje, które ułatwiają znacznie szybsze niż <xref:System.Xml.Xsl.XslTransform> klasy.  
  
> [!NOTE]
>  Mimo że ogólną wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepsze niż <xref:System.Xml.Xsl.XslTransform> klasy <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody <xref:System.Xml.Xsl.XslCompiledTransform> klasy może działać więcej wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> metody <xref:System.Xml.Xsl.XslTransform> klasy pierwszego czasu jest wywoływana w transformacji. Jest to spowodowane plik XSLT, ale muszą być skompilowane, zanim został załadowany. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="security"></a>Zabezpieczenia  
 Domyślnie <xref:System.Xml.Xsl.XslCompiledTransform> klasy wyłącza obsługę XSLT `document()` funkcji i skryptów osadzonych. Te funkcje można włączyć poprzez utworzenie <xref:System.Xml.Xsl.XsltSettings> obiekt, który zawiera funkcje włączone i przekazanie jej do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Poniższy przykład pokazuje, jak włączyć obsługę skryptów i wykonywanie przekształcenia XSLT.  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).  
  
## <a name="new-features"></a>Nowe funkcje  
  
### <a name="temporary-files"></a>Pliki tymczasowe  
 Pliki tymczasowe czasami są generowane podczas XSLT przetwarzania. Jeśli arkusz stylów zawiera bloki skryptu lub jest kompilowany przy użyciu zestawu ustawienia debugowania na wartość true, tymczasowych plików może zostać utworzony w folderze % TEMP %. Mogą wystąpić sytuacje, gdy niektóre pliki tymczasowe nie są usuwane ze względu na problemy dotyczące synchronizacji. Na przykład, jeśli pliki są używane przez bieżącego elementu AppDomain lub przez debuger finalizatora <xref:System.CodeDom.Compiler.TempFileCollection> obiekt nie będzie można je usunąć.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Właściwości można uzyskać dodatkowe Oczyszczanie upewnij się, że wszystkie pliki tymczasowe są usuwane z klienta.  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Pomoc techniczna dla elementu xsl: Output i XmlWriter  
 <xref:System.Xml.Xsl.XslTransform> Klasy ignorowane `xsl:output` ustawień, gdy dane wyjściowe transformacji została wysłana do <xref:System.Xml.XmlWriter> obiektu. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa ma <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> właściwość, która zwraca <xref:System.Xml.XmlWriterSettings> pochodną obiektu zawierającego informacje z danych wyjściowych `xsl:output` element arkusza stylów. <xref:System.Xml.XmlWriterSettings> Obiekt jest używany do tworzenia <xref:System.Xml.XmlWriter> obiektu z prawidłowymi ustawieniami, które mogą być przekazywane do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Poniższy kod C# ilustruje ten problem:  
  
```  
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
  
### <a name="debug-option"></a>Debug — opcja  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasy może wygenerować informacji debugowania, co pozwala na debugowanie arkusza stylów, za pomocą programu Microsoft Visual Studio Debugger. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.  
  
## <a name="behavioral-differences"></a>Różnice w zachowaniu  
  
### <a name="transforming-to-an-xmlreader"></a>Przekształcenie do elementu XmlReader  
 <xref:System.Xml.Xsl.XslTransform> Klasa ma kilka przeciążeń przekształcenia, które zwracają wyniki w postaci przekształcania <xref:System.Xml.XmlReader> obiektu. Te przeciążenia może służyć do ładowania wyników przekształcenie do reprezentacji w pamięci (takie jak <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument>) bez ponoszenia kosztów serializacji i deserializacji wynikowy kod XML drzewa. Poniższy kod C# pokazano, jak możesz załadować wyniki przekształcenia do <xref:System.Xml.XmlDocument> obiektu.  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie obsługuje przekształcania w <xref:System.Xml.XmlReader> obiektu. Jednak zrobić coś podobnego przez przy użyciu <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodę, aby załadować wynikowy kod XML drzewa bezpośrednio z <xref:System.Xml.XmlWriter>. Poniższy kod C# pokazuje sposób wykonania tego samego zadania za pomocą <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>Zachowanie poufne  
 Zalecenie w wersji 1.0 W3C przekształcenia XSL (XSLT) obejmuje obszary, w których implementacja dostawcy może podjąć decyzję sposób obsługi sytuacji. Te obszary są uznawane za poufne zachowanie. Istnieje kilka obszarów gdzie <xref:System.Xml.Xsl.XslCompiledTransform> zachowuje się inaczej niż <xref:System.Xml.Xsl.XslTransform> klasy. Aby uzyskać więcej informacji, zobacz [odwracalne błędy XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).  
  
### <a name="extension-objects-and-script-functions"></a>Obiekty rozszerzeń i funkcji skryptu  
 <xref:System.Xml.Xsl.XslCompiledTransform> wprowadzono dwa nowe ograniczeń dotyczących używania funkcji skryptu:  
  
-   Tylko metody publiczne, może być wywoływana z wyrażenia XPath.  
  
-   Przeciążenia różnią się od siebie nawzajem na podstawie liczby argumentów. Jeśli więcej niż jednego przeciążenia ma taką samą liczbę argumentów, zostanie wygenerowany wyjątek.  
  
 W <xref:System.Xml.Xsl.XslCompiledTransform>powiązania (wyszukiwanie nazw metody) do funkcji skryptu wystąpi w czasie kompilacji i arkusze stylów, które działały z XslTranform może spowodować wyjątek, gdy są one załadowane <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> obsługuje o `msxsl:using` i `msxsl:assembly` elementy podrzędne wewnątrz `msxsl:script` elementu. `msxsl:using` i `msxsl:assembly` elementy są używane do deklarowania dodatkowe przestrzenie nazw i zestawów do użycia w bloku skryptu. Zobacz [skryptu bloki msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> zabrania obiekty rozszerzeń, które mają wiele przeciążeń z taką samą liczbę argumentów.  
  
### <a name="msxml-functions"></a>Funkcje programu MSXML  
 Obsługa dodatkowych funkcji programu MSXML zostały dodane do <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Na poniższej liście opisano nowe i ulepszone funkcje:  
  
-   msxsl:node — Ustaw: <xref:System.Xml.Xsl.XslTransform> wymagany argument [zestaw węzłów funkcji](https://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) funkcji wynikowego fragmentu drzewa. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie ma to wymaganie.  
  
-   msxsl:Version: Ta funkcja jest obsługiwana w <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   Funkcji XPath rozszerzenia: [ms:string-compare — funkcja](https://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc — funkcja](https://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [MS: namespace-funkcji identyfikatora uri](https://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local — nadaj nazwę funkcji](https://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number funkcja](https://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format — Data — funkcja](https://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5), i [ms:format-czasu funkcji](https://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) funkcje są teraz obsługiwane.  
  
-   Powiązane schematu funkcji rozszerzenia XPath: te funkcje nie są obsługiwane natywnie przez <xref:System.Xml.Xsl.XslCompiledTransform>. Jednak może być implementowany jako funkcji rozszerzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
