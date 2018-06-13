---
title: Zestaw XmlSchemaSet schematu kompilacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91835006925f9768c25ad1a984a3b189e3e4c58c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579083"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Zestaw XmlSchemaSet schematu kompilacji
W tym artykule opisano <xref:System.Xml.Schema.XmlSchemaSet>, gdzie schematu XML definition language (XSD) schematów mogą być przechowywane i zweryfikować pamięci podręcznej.  
  
## <a name="the-xmlschemaset-class"></a>Zestaw XmlSchemaSet klasy  
 <xref:System.Xml.Schema.XmlSchemaSet> Jest pamięcią podręczną, gdzie schematu XML definition language (XSD) schematów mogą być przechowywane i sprawdzania poprawności.  
  
 W <xref:System.Xml?displayProperty=nameWithType> wersji 1.0 schematów XML zostały załadowane do <xref:System.Xml.Schema.XmlSchemaCollection> klasy jako biblioteki schematów. W <xref:System.Xml?displayProperty=nameWithType> w wersji 2.0, <xref:System.Xml.XmlValidatingReader> i <xref:System.Xml.Schema.XmlSchemaCollection> klas są przestarzałe i zostało zastąpione przez <xref:System.Xml.XmlReader.Create%2A> metod i <xref:System.Xml.Schema.XmlSchemaSet> odpowiednio klasy.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Został wprowadzony ustalenie szereg problemów z tym standardów zgodności, wydajności i przestarzały format schematu Microsoft XML-danych (XDR).  
  
 Poniżej przedstawiono porównanie <xref:System.Xml.Schema.XmlSchemaCollection> klasy i <xref:System.Xml.Schema.XmlSchemaSet> klasy.  
  
|Kolekcji XmlSchemaCollection|Zestaw XmlSchemaSet|  
|-------------------------|------------------|  
|Obsługuje schematy XDR firmy Microsoft i W3C XML.|Obsługuje tylko schematów W3C XML.|  
|Schematy są kompilowane przy <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metoda jest wywoływana.|Schematy nie są skompilowane, kiedy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda jest wywoływana. Zapewnia to lepszą wydajność, podczas tworzenia biblioteki schematów.|  
|Każdy schematu generuje poszczególnych skompilowanej wersji, która może spowodować "Wyspy schematu." W związku z tym wszystkie zawiera i Importy ograniczone tylko w ramach tego schematu.|Schematy skompilowanych Generowanie pojedynczego schematu logiczne, "zestawu" schematów. Importowane schematy w ramach schematu, które są dodawane do zestawu są bezpośrednio dodać do zbioru samodzielnie. Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.|  
|W kolekcji może istnieć tylko jeden schemat dla docelowego określonego obszaru nazw.|Tak długo, jak to zapobiec konfliktom typu można dodać wiele schematów dla tego samego docelowego obszaru nazw.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrowanie do schematu XmlSchemaSet  
 Poniższy przykład kodu zawiera przewodnik dotyczący migracji do nowego <xref:System.Xml.Schema.XmlSchemaSet> klasy z przestarzałe <xref:System.Xml.Schema.XmlSchemaCollection> klasy. Przykładowy kod przedstawia następujące główne różnice między dwie klasy.  
  
-   W odróżnieniu od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy nie są kompilowane przy wywoływaniu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metody <xref:System.Xml.Schema.XmlSchemaSet> jawnie jest wywoływana w przykładowym kodzie.  
  
-   Aby przejść przez <xref:System.Xml.Schema.XmlSchemaSet>, należy użyć <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniżej znajduje się nieaktualne <xref:System.Xml.Schema.XmlSchemaCollection> przykładowego kodu.  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 Poniżej przedstawiono odpowiednikiem <xref:System.Xml.Schema.XmlSchemaSet> przykładowego kodu.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a>Dodawanie i pobieranie schematów  
 Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. Po dodaniu do schematu <xref:System.Xml.Schema.XmlSchemaSet>, jest on skojarzony z docelową przestrzeń nazw identyfikatora URI. Docelowa przestrzeń nazw albo można określić identyfikatora URI jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody lub jeśli nie docelowego obszaru nazw jest określony, <xref:System.Xml.Schema.XmlSchemaSet> używa docelową przestrzeń nazw zdefiniowana w schemacie.  
  
 Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaSet> służy do wykonywania iteracji <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Właściwości albo zwraca wszystkie <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>, lub podany docelowej przestrzeni nazw parametru zwraca wszystkie <xref:System.Xml.Schema.XmlSchema> obiektów, które należą do docelowego obszaru nazw. Jeśli `null` jest określony jako parametr przestrzeni nazw target <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość zwraca wszystkich schematów bez przestrzeni nazw.  
  
 W poniższym przykładzie dodano `books.xsd` schematu w `http://www.contoso.com/books` przestrzeni nazw do <xref:System.Xml.Schema.XmlSchemaSet>, pobiera wszystkich schematów, które należą do `http://www.contoso.com/books` przestrzeni nazw z <xref:System.Xml.Schema.XmlSchemaSet>, a następnie zapisuje te schematy <xref:System.Console>.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 Aby uzyskać więcej informacji o dodawaniu i pobierania schematów z <xref:System.Xml.Schema.XmlSchemaSet> obiektów, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> — metoda i <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości dokumentacji.  
  
## <a name="compiling-schemas"></a>Kompilowania schematów  
 Schematy w <xref:System.Xml.Schema.XmlSchemaSet> są skompilowane w jeden schemat logicznego przez <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
>  W odróżnieniu od przestarzałe <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy nie są skompilowane, kiedy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda jest wywoływana.  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> pomyślnym wykonaniu metody <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> ma ustawioną wartość `true`.  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwości nie występuje w przypadku edytowania są schematy while w <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizacje indywidualnych schematów w <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone. W związku z tym <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość może być `true` nawet jednego ze schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> zostanie zmieniony, tak długo, jak schematów nie zostały dodane lub usunięte z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 W poniższym przykładzie dodano `books.xsd` pliku <xref:System.Xml.Schema.XmlSchemaSet> , a następnie wywołuje <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 Aby uzyskać więcej informacji na temat kompilowania schematów w <xref:System.Xml.Schema.XmlSchemaSet>, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> dokumentacji metody.  
  
## <a name="reprocessing-schemas"></a>Ponowne przetwarzanie schematów  
 Ponowne przetwarzanie schematu w <xref:System.Xml.Schema.XmlSchemaSet> wykonuje przetwarzania wstępnego czynności wykonywane w schemacie podczas <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana. Jeśli wywołanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody zakończy się pomyślnie, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> ma ustawioną wartość `false`.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Metoda powinna być używana, gdy schemat w <xref:System.Xml.Schema.XmlSchemaSet> została zmodyfikowana po <xref:System.Xml.Schema.XmlSchemaSet> wykonał kompilację.  
  
 Poniższy przykład przedstawia ponownego przetwarzania dodane do schematu <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody. Po <xref:System.Xml.Schema.XmlSchemaSet> została skompilowana przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> — metoda i dodane do schematu <xref:System.Xml.Schema.XmlSchemaSet> zmodyfikowaniu <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość jest ustawiona na `true` nawet wtedy, gdy schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany. Wywoływanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda wykonuje wszystkie przetwarzanie wstępne wykonywane przez <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> — metoda i zestawy <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwości `false`.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 Aby uzyskać więcej informacji na temat ponownego przetwarzania schematu w <xref:System.Xml.Schema.XmlSchemaSet>, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> dokumentacji metody.  
  
## <a name="checking-for-a-schema"></a>Sprawdzanie schematu  
 Można użyć <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> do sprawdzenia, jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda przyjmuje albo docelowej przestrzeni nazw lub <xref:System.Xml.Schema.XmlSchema> obiektu do wyszukania. W obu przypadkach <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda zwraca `true` Jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>; w przeciwnym razie zwraca `false`.  
  
 Aby uzyskać więcej informacji o sprawdzaniu dla schematu, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> dokumentacji metody.  
  
## <a name="removing-schemas"></a>Usuwanie schematów  
 Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda usuwa określony schemat z <xref:System.Xml.Schema.XmlSchemaSet>, podczas gdy <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda usuwa określony schemat i wszystkich schematów importuje z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniższy przykład przedstawia dodawanie wielu schematach do <xref:System.Xml.Schema.XmlSchemaSet>, następnie przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metodę, aby usunąć jedną ze schematów i wszystkich schematów importowania.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 Aby uzyskać więcej informacji na temat usuwania schematów z <xref:System.Xml.Schema.XmlSchemaSet>, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody odwołania dokumentacji.  
  
## <a name="schema-resolution-and-xsimport"></a>Rozdzielczość schematu i xs:import  
 Poniższe przykłady przedstawiają <xref:System.Xml.Schema.XmlSchemaSet> zachowania w przypadku importowania schematów, gdy istnieje wiele schematów dla danej przestrzeni nazw w <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Rozważmy na przykład <xref:System.Xml.Schema.XmlSchemaSet> zawierający wiele schematów dla `http://www.contoso.com` przestrzeni nazw. Schemat z następującymi `xs:import` dyrektywa jest dodawany do <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Próbuje zaimportować schematu dla `http://www.contoso.com` przestrzeni nazw przez załadowanie go z `http://www.contoso.com/schema.xsd` adresu URL. Deklaracja schematu i typy zadeklarowane w schemacie dokumentu są dostępne w schemacie importowania, nawet jeśli istnieją inne dokumenty schematu dla tylko `http://www.contoso.com` przestrzeni nazw w <xref:System.Xml.Schema.XmlSchemaSet>. Jeśli `schema.xsd` pliku nie może znajdować się w lokalizacji `http://www.contoso.com/schema.xsd` adres URL, Brak schematu dla `http://www.contoso.com` przestrzeni nazw jest importowany do importowania schematu.  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML może zostać zweryfikowany względem schematów w <xref:System.Xml.Schema.XmlSchemaSet>. Zweryfikuj dokument XML, dodając schematu <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu lub poprzez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu. <xref:System.Xml.XmlReaderSettings> Obiekt jest następnie używany przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy w celu utworzenia <xref:System.Xml.XmlReader> obiektu i sprawdź poprawność dokumentu XML.  
  
 Aby uzyskać więcej informacji o weryfikacji XML dokumentów za pomocą <xref:System.Xml.Schema.XmlSchemaSet>, zobacz [sprawdzania poprawności schematu XML (XSD) z XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
 [Zestaw XmlSchemaSet jako pamięci podręcznej schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
