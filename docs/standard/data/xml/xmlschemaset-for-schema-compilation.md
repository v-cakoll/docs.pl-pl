---
title: Klasa XmlSchemaSet na potrzeby kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 55347de81c65b7390584415dd29044f4ca4ba02a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709819"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Klasa XmlSchemaSet na potrzeby kompilacji schematu
Opisuje <xref:System.Xml.Schema.XmlSchemaSet>, pamięć podręczną, w której można przechowywać i sprawdzać schematy języka definicji schematu XML (XSD).  
  
## <a name="the-xmlschemaset-class"></a>Klasa XmlSchemaSet  
 <xref:System.Xml.Schema.XmlSchemaSet> to pamięć podręczna, w której schematy języka definicji schematu XML (XSD) mogą być przechowywane i weryfikowane.  
  
 W <xref:System.Xml?displayProperty=nameWithType> w wersji 1,0 schematy XML zostały załadowane do klasy <xref:System.Xml.Schema.XmlSchemaCollection> jako biblioteka schematów. W <xref:System.Xml?displayProperty=nameWithType> w wersji 2,0 <xref:System.Xml.XmlValidatingReader> i <xref:System.Xml.Schema.XmlSchemaCollection> klasy są przestarzałe i zostały zastąpione przez metody <xref:System.Xml.XmlReader.Create%2A> oraz odpowiednio do klasy <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Wprowadzono <xref:System.Xml.Schema.XmlSchemaSet>, aby rozwiązać wiele problemów, w tym zgodność ze standardami, wydajność i przestarzały format schematu danych Microsoft XML (XDR).  
  
 Poniżej znajduje się porównanie klasy <xref:System.Xml.Schema.XmlSchemaCollection> i klasy <xref:System.Xml.Schema.XmlSchemaSet>.  
  
|Klasy XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Obsługuje schematy XDR i W3C XML firmy Microsoft.|Obsługuje tylko schematy W3C XML.|  
|Schematy są kompilowane, gdy wywoływana jest metoda <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.|Schematy nie są kompilowane, gdy wywoływana jest metoda <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>. Zapewnia to poprawę wydajności podczas tworzenia biblioteki schematów.|  
|Każdy schemat generuje konkretną kompilację, która może skutkować "wyspami". W związku z tym wszystkie operacje dołączania i importowania są uwzględniane tylko w tym schemacie.|Skompilowane schematy generują pojedynczy schemat logiczny "zestaw" schematów. Wszystkie zaimportowane schematy w schemacie, które są dodawane do zestawu, są bezpośrednio dodawane do samego zestawu. Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.|  
|W kolekcji może istnieć tylko jeden schemat dla konkretnej przestrzeni nazw.|Można dodać wiele schematów dla tej samej docelowej przestrzeni nazw, o ile nie występują konflikty typów.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrowanie do XmlSchemaSet  
 Poniższy przykład kodu zawiera Przewodnik migracji do nowej klasy <xref:System.Xml.Schema.XmlSchemaSet> z przestarzałej klasy <xref:System.Xml.Schema.XmlSchemaCollection>. Przykład kodu ilustruje następujące główne różnice między tymi dwiema klasami.  
  
- W przeciwieństwie do metody <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> klasy <xref:System.Xml.Schema.XmlSchemaCollection>, schematy nie są kompilowane podczas wywoływania metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> jest jawnie wywoływana w przykładowym kodzie.  
  
- Aby wykonać iterację <xref:System.Xml.Schema.XmlSchemaSet>, należy użyć właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniżej znajduje się przestarzały przykład kodu <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
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
  
 Poniżej przedstawiono odpowiednik przykładu kodu <xref:System.Xml.Schema.XmlSchemaSet>.  
  
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
 Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Po dodaniu schematu do <xref:System.Xml.Schema.XmlSchemaSet>jest on skojarzony z docelowym identyfikatorem URI przestrzeni nazw. Docelowy identyfikator URI przestrzeni nazw może być określony jako parametr metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> lub jeśli nie określono docelowej przestrzeni nazw, <xref:System.Xml.Schema.XmlSchemaSet> używa docelowej przestrzeni nazw zdefiniowanej w schemacie.  
  
 Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Właściwość <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> pozwala na iterację <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>. Właściwość <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> zwraca wszystkie obiekty <xref:System.Xml.Schema.XmlSchema> zawarte w <xref:System.Xml.Schema.XmlSchemaSet>lub, uwzględniając docelowy parametr przestrzeni nazw, zwraca wszystkie obiekty <xref:System.Xml.Schema.XmlSchema> należące do docelowej przestrzeni nazw. Jeśli `null` jest określony jako docelowy parametr przestrzeni nazw, właściwość <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> zwraca wszystkie schematy bez przestrzeni nazw.  
  
 Poniższy przykład dodaje schemat `books.xsd` w przestrzeni nazw `http://www.contoso.com/books` do <xref:System.Xml.Schema.XmlSchemaSet>, pobiera wszystkie schematy należące do przestrzeni nazw `http://www.contoso.com/books` z <xref:System.Xml.Schema.XmlSchemaSet>, a następnie zapisuje te schematy na <xref:System.Console>.  
  
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
  
 Aby uzyskać więcej informacji o dodawaniu i pobieraniu schematów z obiektu <xref:System.Xml.Schema.XmlSchemaSet>, zobacz metodę <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> i dokumentację dotyczącą właściwości <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.  
  
## <a name="compiling-schemas"></a>Kompilowanie schematów  
 Schematy w <xref:System.Xml.Schema.XmlSchemaSet> są kompilowane do jednego schematu logicznego za pomocą metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
> W przeciwieństwie do przestarzałej klasy <xref:System.Xml.Schema.XmlSchemaCollection>, schematy nie są kompilowane, gdy wywoływana jest metoda <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda zostanie wykonana pomyślnie, właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `true`.  
  
> [!NOTE]
> Nie dotyczy właściwości <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A>, jeśli schematy są edytowane podczas <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizacje poszczególnych schematów w <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone. W związku z tym Właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> może być `true`, mimo że jeden z schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> został zmieniony, o ile żadne schematy nie zostały dodane lub usunięte z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniższy przykład dodaje `books.xsd` plik do <xref:System.Xml.Schema.XmlSchemaSet> a następnie wywołuje metodę <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.  
  
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
  
 Więcej informacji o kompilowaniu schematów w <xref:System.Xml.Schema.XmlSchemaSet>można znaleźć w dokumentacji dotyczącej metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.  
  
## <a name="reprocessing-schemas"></a>Przeprzetwarzanie schematów  
 Przeprzetwarzanie schematu w <xref:System.Xml.Schema.XmlSchemaSet> wykonuje wszystkie kroki przetwarzania wstępnego wykonane na schemacie po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Jeśli wywołanie metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> powiodło się, właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `false`.  
  
 Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> powinna być używana, gdy schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany po wykonaniu kompilacji przez <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniższy przykład ilustruje reprzetwarzanie schematu dodanego do <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>. Po skompilowaniu <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>, a schemat dodany do <xref:System.Xml.Schema.XmlSchemaSet> jest modyfikowany, właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> zostanie ustawiona na `true`, mimo że schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany. Wywołanie metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> wykonuje wszystkie przetwarzanie wstępne wykonywane przez metodę <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> i ustawia właściwość <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> na `false`.  
  
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
  
 Aby uzyskać więcej informacji na temat ponownego przetwarzania schematu w <xref:System.Xml.Schema.XmlSchemaSet>, zobacz dokumentację referencyjną metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.  
  
## <a name="checking-for-a-schema"></a>Sprawdzanie schematu  
 Można użyć metody <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet>, aby sprawdzić, czy schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>. Metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> przyjmuje docelową przestrzeń nazw lub obiekt <xref:System.Xml.Schema.XmlSchema> do sprawdzenia. W obu przypadkach Metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> zwraca `true`, jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>; w przeciwnym razie zwraca `false`.  
  
 Więcej informacji o sprawdzaniu schematu znajduje się w dokumentacji dotyczącej metody <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.  
  
## <a name="removing-schemas"></a>Usuwanie schematów  
 Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Metoda <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> usuwa określony schemat z <xref:System.Xml.Schema.XmlSchemaSet>, podczas gdy metoda <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> usuwa określony schemat i wszystkie schematy importowane z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniższy przykład ilustruje Dodawanie wielu schematów do <xref:System.Xml.Schema.XmlSchemaSet>, a następnie użycie metody <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> w celu usunięcia jednego ze schematów i wszystkich importowanych schematów.  
  
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
  
 Aby uzyskać więcej informacji na temat usuwania schematów z <xref:System.Xml.Schema.XmlSchemaSet>, zapoznaj się z dokumentacją dotyczącą metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.  
  
## <a name="schema-resolution-and-xsimport"></a>Rozdzielczość schematu i xs: import  
 W poniższych przykładach opisano zachowanie <xref:System.Xml.Schema.XmlSchemaSet> w przypadku importowania schematów, gdy w <xref:System.Xml.Schema.XmlSchemaSet>istnieje wiele schematów dla danego obszaru nazw.  
  
 Rozważmy na przykład <xref:System.Xml.Schema.XmlSchemaSet>, który zawiera wiele schematów dla przestrzeni nazw `http://www.contoso.com`. Schemat o następującej `xs:import` dyrektywie zostanie dodany do <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> próbuje zaimportować schemat przestrzeni nazw `http://www.contoso.com` przez załadowanie go z adresu URL `http://www.contoso.com/schema.xsd`. Tylko Deklaracja schematu i typy zadeklarowane w dokumencie schematu są dostępne w schemacie importowania, chociaż istnieją inne dokumenty schematu dla przestrzeni nazw `http://www.contoso.com` w <xref:System.Xml.Schema.XmlSchemaSet>. Jeśli nie można zlokalizować pliku `schema.xsd` pod adresem URL `http://www.contoso.com/schema.xsd`, żaden schemat przestrzeni nazw `http://www.contoso.com` nie zostanie zaimportowany do schematu importowania.  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML można sprawdzić pod kątem schematów w <xref:System.Xml.Schema.XmlSchemaSet>. Sprawdzanie poprawności dokumentu XML przez dodanie schematu do właściwości <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>obiektu <xref:System.Xml.XmlReaderSettings> lub przez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do właściwości <xref:System.Xml.XmlReaderSettings.Schemas%2A> obiektu <xref:System.Xml.XmlReaderSettings>. Obiekt <xref:System.Xml.XmlReaderSettings> jest następnie używany przez metodę <xref:System.Xml.XmlReader.Create%2A> klasy <xref:System.Xml.XmlReader> do tworzenia obiektu <xref:System.Xml.XmlReader> i sprawdzania poprawności dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat walidacji dokumentów XML przy użyciu <xref:System.Xml.Schema.XmlSchemaSet>, zobacz [Walidacja schematu XML (XSD) z](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)zestawem XmlSchemaSet.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [XmlSchemaSet jako pamięć podręczna schematów](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
