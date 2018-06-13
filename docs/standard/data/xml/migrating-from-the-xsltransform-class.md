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
ms.openlocfilehash: bac8d1496463d1224021270347c9480e7ce391e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577401"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrowanie z klasy XslTransform
Architektura XSLT został przeprojektowany w [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] wersji. <xref:System.Xml.Xsl.XslTransform> Klasa została zastąpiona przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.  
  
 W poniższych sekcjach opisano niektóre główne różnice między <xref:System.Xml.Xsl.XslCompiledTransform> i <xref:System.Xml.Xsl.XslTransform> klasy.  
  
## <a name="performance"></a>Wydajność  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera wiele ulepszeń wydajności. Nowe procesorze XSLT kompiluje arkusz stylów XSLT do wspólnego formatu pośredniego, podobnie jak w przypadku języków programowania czego środowisko uruchomieniowe języka wspólnego (CLR). Gdy arkusz stylów jest kompilowana, można w pamięci podręcznej i ponownie.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera również inne funkcje optymalizacji, które ułatwiają znacznie szybsze niż <xref:System.Xml.Xsl.XslTransform> klasy.  
  
> [!NOTE]
>  Mimo że ogólną wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepszym rozwiązaniem niż <xref:System.Xml.Xsl.XslTransform> klasy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody <xref:System.Xml.Xsl.XslCompiledTransform> klasy może zapewnić więcej wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> metody <xref:System.Xml.Xsl.XslTransform> klasy pierwszy czasu wywoływana jest transformację. Jest to spowodowane musi zostać skompilowany plik XSLT, przed jego załadowaniem. Aby uzyskać więcej informacji, zobacz następującym wpisie w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="security"></a>Zabezpieczenia  
 Domyślnie <xref:System.Xml.Xsl.XslCompiledTransform> klasy wyłącza obsługę XSLT `document()` funkcji i osadzonych skryptów. Te funkcje można włączyć, tworząc <xref:System.Xml.Xsl.XsltSettings> obiektu, który ma funkcje włączone i nastąpiło przejście do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Poniższy przykład pokazuje, jak włączyć obsługę skryptów i przekształcenie XSLT.  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).  
  
## <a name="new-features"></a>Nowe funkcje  
  
### <a name="temporary-files"></a>Pliki tymczasowe  
 Pliki tymczasowe czasami są generowane podczas XSLT przetwarzania. Jeśli arkusz stylów zawiera bloki skryptu lub jest on skompilowany z wartością ustawienia debugowania można tworzyć wartość true, tymczasowe pliki w folderze % TEMP %. Mogą wystąpić sytuacje, gdy niektóre pliki tymczasowe nie są usuwane ze względu na problemy dotyczące synchronizacji. Na przykład, jeśli pliki znajdują się w używany w bieżącym elemencie AppDomain lub przez debuger finalizatora <xref:System.CodeDom.Compiler.TempFileCollection> obiektu nie będzie można je usunąć.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Właściwości umożliwia dodatkowe oczyszczania upewnij się, że wszystkie pliki tymczasowe są usuwane z klienta.  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Obsługa elementu xsl: Output i XmlWriter  
 <xref:System.Xml.Xsl.XslTransform> Klasy ignorowane `xsl:output` ustawień, gdy przekształcenie dane wyjściowe zostały wysłane do <xref:System.Xml.XmlWriter> obiektu. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa ma <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> właściwości, która zwraca <xref:System.Xml.XmlWriterSettings> obiekt zawierający dane wyjściowe pochodzące z `xsl:output` element arkusza stylów. <xref:System.Xml.XmlWriterSettings> Obiekt jest używany do tworzenia <xref:System.Xml.XmlWriter> obiektu o poprawne ustawienia, które mogą zostać przekazane do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Poniższy kod C# ilustruje tego zachowania:  
  
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
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasy mogą generować informacji o debugowaniu, dzięki czemu można debugować arkusz stylów z debuger Microsoft Visual Studio. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.  
  
## <a name="behavioral-differences"></a>Różnice funkcjonalne  
  
### <a name="transforming-to-an-xmlreader"></a>Przekształcanie na element XmlReader  
 <xref:System.Xml.Xsl.XslTransform> Klasa ma kilka przeciążeń przekształcania, które zwracają wyniki w postaci przekształcania <xref:System.Xml.XmlReader> obiektu. Te przeciążenia może służyć do ładowanie wyników transformacji do reprezentacji w pamięci (takie jak <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument>) bez ponoszenia obciążenie serializacji i deserializacji wynikowy kod XML drzewa. Poniższy kod C# pokazano, jak można załadować wyników transformacji do <xref:System.Xml.XmlDocument> obiektu.  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie obsługuje transformacji do <xref:System.Xml.XmlReader> obiektu. Jednak można zrobić coś podobnego przez przy użyciu <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodę, aby załadować wynikowy kod XML drzewa bezpośrednio z <xref:System.Xml.XmlWriter>. Poniższy kod C# przedstawia sposób wykonania tego samego zadania przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>Zachowanie DACL  
 Zalecenia w wersji 1.0 W3C transformacji XSL (XSLT) obejmuje obszary, w których implementacji dostawcy może decyzję dotyczącą sposobu obsługi sytuacji. Te obszary są uważane za DACL zachowanie. Istnieje kilka obszarów gdzie <xref:System.Xml.Xsl.XslCompiledTransform> zachowuje się inaczej niż <xref:System.Xml.Xsl.XslTransform> klasy. Aby uzyskać więcej informacji, zobacz [możliwych do odzyskania błędy XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).  
  
### <a name="extension-objects-and-script-functions"></a>Rozszerzenia obiektów i funkcji skryptu  
 <xref:System.Xml.Xsl.XslCompiledTransform> wprowadzono dwie nowe ograniczenia dotyczące stosowania funkcji skryptu:  
  
-   Może być wywoływana tylko metody publicznej z wyrażenia XPath.  
  
-   Przeciążenia różnią się od siebie na podstawie liczby argumentów. Jeśli więcej niż jednego przeciążenia ma taką samą liczbę argumentów, zostanie zgłoszony wyjątek.  
  
 W <xref:System.Xml.Xsl.XslCompiledTransform>powiązania (wyszukiwanie nazwy metody) do skryptu funkcji występuje w czasie kompilacji i arkusze stylów, które działały z XslTranform może spowodować wyjątek, gdy są załadowane z <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> obsługuje posiadanie `msxsl:using` i `msxsl:assembly` elementy podrzędne w `msxsl:script` elementu. `msxsl:using` i `msxsl:assembly` elementy są używane do deklarowania dodatkowe przestrzenie nazw i zestawów do użycia w bloku skryptu. Zobacz [przy użyciu bloków skryptu msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Zabrania używania obiektów rozszerzenia, które mają wielu przeładowań z tą samą liczbą argumentów.  
  
### <a name="msxml-functions"></a>Funkcje programu MSXML  
 Obsługa dodatkowych funkcji MSXML zostały dodane do <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Na poniższej liście opisano nowe i ulepszone funkcje:  
  
-   msxsl:node — ustawianie: <xref:System.Xml.Xsl.XslTransform> wymagany argument [zestaw węzłów funkcji](https://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) funkcję, która ma być wynikowego fragmentu drzewa. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie ma tego wymogu.  
  
-   msxsl:Version: Ta funkcja jest obsługiwana w <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   Funkcje rozszerzeń XPath: [ms:string — compare — funkcja](https://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc funkcji](https://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace — uri funkcji](https://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local — nazwy funkcji](https://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number funkcja](https://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-Data funkcja](https://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5), i [ms:format-czasu funkcji](https://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) funkcje są teraz obsługiwane.  
  
-   Powiązane schematu funkcje rozszerzenia XPath: te funkcje nie są obsługiwane natywnie przez <xref:System.Xml.Xsl.XslCompiledTransform>. Jednak może być zaimplementowany jako funkcje rozszerzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
