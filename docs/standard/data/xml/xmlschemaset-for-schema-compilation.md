---
title: Klasa XmlSchemaSet na potrzeby kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e05b09d5ce788b9a3da262d5890a0694b49375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969030"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Klasa XmlSchemaSet na potrzeby kompilacji schematu
Opisuje pamięć podręczną, w której można przechowywać i sprawdzać schematy języka definicji schematu XML (XSD). <xref:System.Xml.Schema.XmlSchemaSet>  
  
## <a name="the-xmlschemaset-class"></a>Klasa XmlSchemaSet  
 Jest <xref:System.Xml.Schema.XmlSchemaSet> pamięcią podręczną, w której schematy języka definicji schematu XML (XSD) mogą być przechowywane i weryfikowane.  
  
 W <xref:System.Xml?displayProperty=nameWithType> wersji 1,0 schematy XML zostały załadowane <xref:System.Xml.Schema.XmlSchemaCollection> do klasy jako biblioteka schematów. W <xref:System.Xml?displayProperty=nameWithType> wersji 2,0 <xref:System.Xml.XmlValidatingReader> , i <xref:System.Xml.Schema.XmlSchemaCollection> klasy są <xref:System.Xml.XmlReader.Create%2A> przestarzałe i zostały zastąpione metodami oraz <xref:System.Xml.Schema.XmlSchemaSet> klasą.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Wprowadzono rozwiązanie do rozwiązywania problemów, takich jak zgodność ze standardami, wydajność i przestarzały format schematu Microsoft XML — zmniejszone (XDR).  
  
 Poniżej znajduje się porównanie <xref:System.Xml.Schema.XmlSchemaCollection> klasy <xref:System.Xml.Schema.XmlSchemaSet> i klasy.  
  
|Klasy XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Obsługuje schematy XDR i W3C XML firmy Microsoft.|Obsługuje tylko schematy W3C XML.|  
|Schematy są kompilowane, <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> gdy wywoływana jest metoda.|Schematy nie są kompilowane, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> gdy wywoływana jest metoda. Zapewnia to poprawę wydajności podczas tworzenia biblioteki schematów.|  
|Każdy schemat generuje konkretną kompilację, która może skutkować "wyspami". W związku z tym wszystkie operacje dołączania i importowania są uwzględniane tylko w tym schemacie.|Skompilowane schematy generują pojedynczy schemat logiczny "zestaw" schematów. Wszystkie zaimportowane schematy w schemacie, które są dodawane do zestawu, są bezpośrednio dodawane do samego zestawu. Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.|  
|W kolekcji może istnieć tylko jeden schemat dla konkretnej przestrzeni nazw.|Można dodać wiele schematów dla tej samej docelowej przestrzeni nazw, o ile nie występują konflikty typów.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrowanie do XmlSchemaSet  
 Poniższy przykład kodu zawiera Przewodnik migracji do nowej <xref:System.Xml.Schema.XmlSchemaSet> klasy z klasy przestarzałej. <xref:System.Xml.Schema.XmlSchemaCollection> Przykład kodu ilustruje następujące główne różnice między tymi dwiema klasami.  
  
- W przeciwieństwie <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> do metody <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> nie są kompilowane podczas <xref:System.Xml.Schema.XmlSchemaSet>wywoływania metody. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda<xref:System.Xml.Schema.XmlSchemaSet> jest jawnie wywoływana w przykładowym kodzie.  
  
- Aby wykonać iterację <xref:System.Xml.Schema.XmlSchemaSet>w <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> programie, należy użyć właściwości <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Poniżej znajduje się przestarzały <xref:System.Xml.Schema.XmlSchemaCollection> przykład kodu.  
  
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
  
 Poniżej znajduje się odpowiedni <xref:System.Xml.Schema.XmlSchemaSet> przykładowy kod.  
  
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
 Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>przy użyciu. Gdy schemat zostanie dodany do elementu <xref:System.Xml.Schema.XmlSchemaSet>, jest on skojarzony z docelowym identyfikatorem URI przestrzeni nazw. Docelowy identyfikator URI przestrzeni nazw może być określony jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody lub jeśli nie określono docelowej przestrzeni nazw <xref:System.Xml.Schema.XmlSchemaSet> , używa docelowej przestrzeni nazw zdefiniowanej w schemacie.  
  
 Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> użycia właściwości <xref:System.Xml.Schema.XmlSchemaSet>. Właściwość elementu umożliwia wykonywanie iteracji względem <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> Właściwość zwraca <xref:System.Xml.Schema.XmlSchemaSet>wszystkie obiekty zawarte w, lub, pod <xref:System.Xml.Schema.XmlSchema> którym znajduje się docelowy parametr przestrzeni nazw, zwraca wszystkie obiekty należące do docelowej przestrzeni nazw. <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Jeśli `null` jest określony jako docelowy parametr przestrzeni nazw <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> , właściwość zwraca wszystkie schematy bez przestrzeni nazw.  
  
 `books.xsd` Poniższy przykład dodaje schemat `http://www.contoso.com/books` w przestrzeni nazw do <xref:System.Xml.Schema.XmlSchemaSet>elementu `http://www.contoso.com/books` , pobiera wszystkie <xref:System.Xml.Schema.XmlSchemaSet>schematy należące do <xref:System.Console>przestrzeni nazw z, a następnie zapisuje te schematy do.  
  
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
  
 Aby uzyskać więcej informacji o dodawaniu i pobieraniu <xref:System.Xml.Schema.XmlSchemaSet> schematów z obiektu, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> zapoznaj się <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> z dokumentacją dotyczącą metody i odwołania do właściwości.  
  
## <a name="compiling-schemas"></a>Kompilowanie schematów  
 Schematy w elemencie <xref:System.Xml.Schema.XmlSchemaSet> są kompilowane do jednego schematu logicznego <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> za pomocą metody <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
> W przeciwieństwie do <xref:System.Xml.Schema.XmlSchemaCollection> przestarzałej klasy, schematy nie są kompilowane <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> , gdy wywoływana jest metoda.  
  
 Jeśli metoda zostanie wykonana pomyślnie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , właściwość `true`jest ustawiona na. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
  
> [!NOTE]
> Nie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> ma to żadnego oddziaływania, jeśli schematy są edytowane <xref:System.Xml.Schema.XmlSchemaSet>w trakcie. Aktualizacje poszczególnych schematów w programie <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone. <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> W związku z tym właściwość może być `true` nawet pomimo tego, że jeden z schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> został zmieniony, o ile <xref:System.Xml.Schema.XmlSchemaSet>żadne schematy nie zostały dodane lub usunięte z.  
  
 Poniższy przykład dodaje `books.xsd` plik <xref:System.Xml.Schema.XmlSchemaSet> do a następnie wywołuje <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodę.  
  
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
  
 Więcej informacji o kompilowaniu schematów w programie <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> znajduje się w dokumentacji dotyczącej metod.  
  
## <a name="reprocessing-schemas"></a>Przeprzetwarzanie schematów  
 Przeprzetwarzanie schematu w programie <xref:System.Xml.Schema.XmlSchemaSet> wykonuje wszystkie kroki przetwarzania wstępnego wykonane na schemacie, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> gdy wywoływana <xref:System.Xml.Schema.XmlSchemaSet> jest metoda obiektu. Jeśli wywołanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody zakończyło się pomyślnie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , właściwość <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `false`.  
  
 Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> powinna być używana, gdy schemat <xref:System.Xml.Schema.XmlSchemaSet> w programie <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany po wykonaniu kompilacji.  
  
 Poniższy przykład ilustruje przetworzenie schematu dodanego do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody przy użyciu. <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> `true` <xref:System.Xml.Schema.XmlSchemaSet> Po skompilowaniu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> przy użyciu metody, a schemat dodany do elementu jest modyfikowany, właściwość jest ustawiona na, nawet jeśli schemat w został zmodyfikowany. <xref:System.Xml.Schema.XmlSchemaSet> Wywołanie metody wykonuje wszystkie przetwarzanie wstępne wykonywane <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> przez <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> metodę i ustawia właściwość na `false`. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
  
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
  
 Aby uzyskać więcej informacji na temat ponownego przetwarzania schematu w programie <xref:System.Xml.Schema.XmlSchemaSet>, <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Zobacz dokumentację referencyjną metody.  
  
## <a name="checking-for-a-schema"></a>Sprawdzanie schematu  
 Można użyć <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metody, <xref:System.Xml.Schema.XmlSchemaSet> aby sprawdzić, czy <xref:System.Xml.Schema.XmlSchemaSet>schemat jest zawarty w. Metoda przyjmuje docelowy obszar nazw <xref:System.Xml.Schema.XmlSchema> lub obiekt, który ma zostać wyszukany. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> W obu przypadkach <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda zwraca `true` , jeśli <xref:System.Xml.Schema.XmlSchemaSet>schemat jest zawarty w; w przeciwnym razie zwraca `false`.  
  
 Aby uzyskać więcej informacji na temat sprawdzania schematu, zapoznaj <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> się z dokumentacją dotyczącą metod.  
  
## <a name="removing-schemas"></a>Usuwanie schematów  
 <xref:System.Xml.Schema.XmlSchemaSet> Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> używania metod <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>i. Metoda usuwa określony schemat <xref:System.Xml.Schema.XmlSchemaSet>z, podczas gdy <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> Metoda usuwa określony schemat i wszystkie schematy importowane z programu <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
  
 Poniższy przykład ilustruje Dodawanie wielu schematów do obiektu <xref:System.Xml.Schema.XmlSchemaSet>, a następnie <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> za pomocą metody usuwania jednego ze schematów i wszystkich importowanych schematów.  
  
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
  
 Aby uzyskać więcej informacji na temat usuwania schematów <xref:System.Xml.Schema.XmlSchemaSet>z programu, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> zobacz <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> dokumentację dotyczącą metod i.  
  
## <a name="schema-resolution-and-xsimport"></a>Rozdzielczość schematu i xs: import  
 W poniższych przykładach opisano <xref:System.Xml.Schema.XmlSchemaSet> zachowanie importowania schematów, <xref:System.Xml.Schema.XmlSchemaSet>gdy istnieje wiele schematów dla danego obszaru nazw.  
  
 Rozważmy <xref:System.Xml.Schema.XmlSchemaSet> na przykład, że zawiera wiele schematów `http://www.contoso.com` dla przestrzeni nazw. Schemat z poniższą `xs:import` dyrektywą zostanie dodany <xref:System.Xml.Schema.XmlSchemaSet>do.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 Próbuje zaimportować schemat `http://www.contoso.com` dla przestrzeni nazw `http://www.contoso.com/schema.xsd` przez załadowanie go z adresu URL. <xref:System.Xml.Schema.XmlSchemaSet> Tylko Deklaracja schematu i typy zadeklarowane w dokumencie schematu są dostępne w schemacie importowania, chociaż istnieją inne dokumenty schematu dla `http://www.contoso.com` przestrzeni nazw <xref:System.Xml.Schema.XmlSchemaSet>w. Jeśli plik nie może znajdować się `http://www.contoso.com/schema.xsd` pod adresem URL `http://www.contoso.com` , żaden schemat przestrzeni nazw nie zostanie zaimportowany do schematu importowania. `schema.xsd`  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML można sprawdzić pod kątem schematów w <xref:System.Xml.Schema.XmlSchemaSet>. Sprawdzanie poprawności dokumentu XML przez dodanie <xref:System.Xml.Schema.XmlSchemaSet> schematu do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> <xref:System.Xml.XmlReaderSettings.Schemas%2A> obiektu lub <xref:System.Xml.XmlReaderSettings> poprzez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do właściwości obiektu. Obiekt jest następnie używany <xref:System.Xml.XmlReader.Create%2A> przez metodę <xref:System.Xml.XmlReader> klasy w celu utworzenia <xref:System.Xml.XmlReader> obiektu i zweryfikowania dokumentu XML. <xref:System.Xml.XmlReaderSettings>  
  
 Aby uzyskać więcej informacji na temat walidacji dokumentów <xref:System.Xml.Schema.XmlSchemaSet>XML przy użyciu, zobacz [Walidacja schematu XML (XSD) z](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)zestawem XmlSchemaSet.  
  
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
