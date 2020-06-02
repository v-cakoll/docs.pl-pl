---
title: Klasa XmlSchemaSet na potrzeby kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 44850755c41b212e88e0b90dd3b016f96a0af96d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290230"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Klasa XmlSchemaSet na potrzeby kompilacji schematu
Opisuje <xref:System.Xml.Schema.XmlSchemaSet> pamięć podręczną, w której można przechowywać i sprawdzać schematy języka definicji schematu XML (XSD).  
  
## <a name="the-xmlschemaset-class"></a>Klasa XmlSchemaSet  
 <xref:System.Xml.Schema.XmlSchemaSet>Jest pamięcią podręczną, w której schematy języka definicji schematu XML (XSD) mogą być przechowywane i weryfikowane.  
  
 W <xref:System.Xml?displayProperty=nameWithType> wersji 1,0 schematy XML zostały załadowane do <xref:System.Xml.Schema.XmlSchemaCollection> klasy jako biblioteka schematów. W <xref:System.Xml?displayProperty=nameWithType> wersji 2,0, <xref:System.Xml.XmlValidatingReader> i <xref:System.Xml.Schema.XmlSchemaCollection> klasy są przestarzałe i zostały zastąpione <xref:System.Xml.XmlReader.Create%2A> metodami oraz <xref:System.Xml.Schema.XmlSchemaSet> klasą.  
  
 Wprowadzono <xref:System.Xml.Schema.XmlSchemaSet> rozwiązanie do rozwiązywania problemów, takich jak zgodność ze standardami, wydajność i przestarzały format schematu Microsoft XML — zmniejszone (XDR).  
  
 Poniżej znajduje się porównanie <xref:System.Xml.Schema.XmlSchemaCollection> klasy i <xref:System.Xml.Schema.XmlSchemaSet> klasy.  
  
|Klasy XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Obsługuje schematy XDR i W3C XML firmy Microsoft.|Obsługuje tylko schematy W3C XML.|  
|Schematy są kompilowane, gdy <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> wywoływana jest metoda.|Schematy nie są kompilowane, gdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> wywoływana jest metoda. Zapewnia to poprawę wydajności podczas tworzenia biblioteki schematów.|  
|Każdy schemat generuje konkretną kompilację, która może skutkować "wyspami". W związku z tym wszystkie operacje dołączania i importowania są uwzględniane tylko w tym schemacie.|Skompilowane schematy generują pojedynczy schemat logiczny "zestaw" schematów. Wszystkie zaimportowane schematy w schemacie, które są dodawane do zestawu, są bezpośrednio dodawane do samego zestawu. Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.|  
|W kolekcji może istnieć tylko jeden schemat dla konkretnej przestrzeni nazw.|Można dodać wiele schematów dla tej samej docelowej przestrzeni nazw, o ile nie występują konflikty typów.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrowanie do XmlSchemaSet  
 Poniższy przykład kodu zawiera Przewodnik migracji do nowej <xref:System.Xml.Schema.XmlSchemaSet> klasy z klasy przestarzałej <xref:System.Xml.Schema.XmlSchemaCollection> . Przykład kodu ilustruje następujące główne różnice między tymi dwiema klasami.  
  
- W przeciwieństwie do <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy nie są kompilowane podczas wywoływania <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>Metoda <xref:System.Xml.Schema.XmlSchemaSet> jest jawnie wywoływana w przykładowym kodzie.  
  
- Aby wykonać iterację w <xref:System.Xml.Schema.XmlSchemaSet> programie, należy użyć <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości <xref:System.Xml.Schema.XmlSchemaSet> .  
  
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
 Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> metody przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> . Gdy schemat zostanie dodany do elementu <xref:System.Xml.Schema.XmlSchemaSet> , jest on skojarzony z docelowym identyfikatorem URI przestrzeni nazw. Docelowy identyfikator URI przestrzeni nazw może być określony jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody lub jeśli nie określono docelowej przestrzeni nazw, <xref:System.Xml.Schema.XmlSchemaSet> używa docelowej przestrzeni nazw zdefiniowanej w schemacie.  
  
 Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> użycia <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>Właściwość elementu umożliwia wykonywanie <xref:System.Xml.Schema.XmlSchemaSet> iteracji względem <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>Właściwość zwraca wszystkie <xref:System.Xml.Schema.XmlSchema> obiekty zawarte w <xref:System.Xml.Schema.XmlSchemaSet> , lub, pod którym znajduje się docelowy parametr przestrzeni nazw, zwraca wszystkie <xref:System.Xml.Schema.XmlSchema> obiekty należące do docelowej przestrzeni nazw. Jeśli `null` jest określony jako docelowy parametr przestrzeni nazw, <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Właściwość zwraca wszystkie schematy bez przestrzeni nazw.  
  
 Poniższy przykład dodaje `books.xsd` schemat w `http://www.contoso.com/books` przestrzeni nazw do elementu <xref:System.Xml.Schema.XmlSchemaSet> , pobiera wszystkie schematy należące do `http://www.contoso.com/books` przestrzeni nazw z <xref:System.Xml.Schema.XmlSchemaSet> , a następnie zapisuje te schematy do <xref:System.Console> .  
  
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
  
 Aby uzyskać więcej informacji o dodawaniu i pobieraniu schematów z <xref:System.Xml.Schema.XmlSchemaSet> obiektu, zapoznaj się z <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> dokumentacją dotyczącą metody i odwołania do właściwości.  
  
## <a name="compiling-schemas"></a>Kompilowanie schematów  
 Schematy w elemencie <xref:System.Xml.Schema.XmlSchemaSet> są kompilowane do jednego schematu logicznego za pomocą <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> .  
  
> [!NOTE]
> W przeciwieństwie do przestarzałej <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy nie są kompilowane, gdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> wywoływana jest metoda.  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda zostanie wykonana pomyślnie, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `true` .  
  
> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A>Nie ma to żadnego oddziaływania, jeśli schematy są edytowane w trakcie <xref:System.Xml.Schema.XmlSchemaSet> . Aktualizacje poszczególnych schematów w programie <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone. W związku z tym <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwość może być `true` nawet pomimo tego, że jeden z schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> został zmieniony, o ile żadne schematy nie zostały dodane lub usunięte z <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Poniższy przykład dodaje `books.xsd` plik do <xref:System.Xml.Schema.XmlSchemaSet> a następnie wywołuje <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodę.  
  
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
  
 Więcej informacji o kompilowaniu schematów w programie <xref:System.Xml.Schema.XmlSchemaSet> znajduje się w <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> dokumentacji dotyczącej metod.  
  
## <a name="reprocessing-schemas"></a>Przeprzetwarzanie schematów  
 Przeprzetwarzanie schematu w programie <xref:System.Xml.Schema.XmlSchemaSet> wykonuje wszystkie kroki przetwarzania wstępnego wykonane na schemacie, gdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> wywoływana jest metoda obiektu. Jeśli wywołanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody zakończyło się pomyślnie, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaSet> jest ustawiona na `false` .  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>Metoda powinna być używana, gdy schemat w programie <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany po <xref:System.Xml.Schema.XmlSchemaSet> wykonaniu kompilacji.  
  
 Poniższy przykład ilustruje przetworzenie schematu dodanego do <xref:System.Xml.Schema.XmlSchemaSet> metody przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> . Po <xref:System.Xml.Schema.XmlSchemaSet> skompilowaniu przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody, a schemat dodany do elementu <xref:System.Xml.Schema.XmlSchemaSet> jest modyfikowany, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwość jest ustawiona na, `true` nawet jeśli schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany. Wywołanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody wykonuje wszystkie przetwarzanie wstępne wykonywane przez <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodę i ustawia <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwość na `false` .  
  
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
  
 Aby uzyskać więcej informacji na temat ponownego przetwarzania schematu w programie <xref:System.Xml.Schema.XmlSchemaSet> , zobacz <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> dokumentację referencyjną metody.  
  
## <a name="checking-for-a-schema"></a>Sprawdzanie schematu  
 Można użyć <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metody, <xref:System.Xml.Schema.XmlSchemaSet> Aby sprawdzić, czy schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>Metoda przyjmuje docelowy obszar nazw lub <xref:System.Xml.Schema.XmlSchema> obiekt, który ma zostać wyszukany. W obu przypadkach <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda zwraca, `true` Jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet> ; w przeciwnym razie zwraca `false` .  
  
 Aby uzyskać więcej informacji na temat sprawdzania schematu, zapoznaj się z <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> dokumentacją dotyczącą metod.  
  
## <a name="removing-schemas"></a>Usuwanie schematów  
 Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet> używania <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metod i <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>Metoda usuwa określony schemat z <xref:System.Xml.Schema.XmlSchemaSet> , podczas gdy <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> Metoda usuwa określony schemat i wszystkie schematy importowane z programu <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Poniższy przykład ilustruje Dodawanie wielu schematów do obiektu <xref:System.Xml.Schema.XmlSchemaSet> , a następnie za pomocą <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody usuwania jednego ze schematów i wszystkich importowanych schematów.  
  
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
  
 Aby uzyskać więcej informacji na temat usuwania schematów z programu <xref:System.Xml.Schema.XmlSchemaSet> , <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Zobacz <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> dokumentację dotyczącą metod i.  
  
## <a name="schema-resolution-and-xsimport"></a>Rozdzielczość schematu i xs: import  
 W poniższych przykładach opisano <xref:System.Xml.Schema.XmlSchemaSet> zachowanie importowania schematów, gdy istnieje wiele schematów dla danego obszaru nazw <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Rozważmy na przykład, <xref:System.Xml.Schema.XmlSchemaSet> że zawiera wiele schematów dla `http://www.contoso.com` przestrzeni nazw. Schemat z poniższą `xs:import` dyrektywą zostanie dodany do <xref:System.Xml.Schema.XmlSchemaSet> .  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet>Próbuje zaimportować schemat dla `http://www.contoso.com` przestrzeni nazw przez załadowanie go z `http://www.contoso.com/schema.xsd` adresu URL. Tylko Deklaracja schematu i typy zadeklarowane w dokumencie schematu są dostępne w schemacie importowania, chociaż istnieją inne dokumenty schematu dla `http://www.contoso.com` przestrzeni nazw w <xref:System.Xml.Schema.XmlSchemaSet> . Jeśli `schema.xsd` plik nie może znajdować się pod `http://www.contoso.com/schema.xsd` adresem URL, żaden schemat `http://www.contoso.com` przestrzeni nazw nie zostanie zaimportowany do schematu importowania.  
  
## <a name="validating-xml-documents"></a>Sprawdzanie poprawności dokumentów XML  
 Dokumenty XML można sprawdzić pod kątem schematów w <xref:System.Xml.Schema.XmlSchemaSet> . Sprawdzanie poprawności dokumentu XML przez dodanie schematu do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> obiektu lub poprzez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> obiektu. <xref:System.Xml.XmlReaderSettings>Obiekt jest następnie używany przez <xref:System.Xml.XmlReader.Create%2A> metodę <xref:System.Xml.XmlReader> klasy w celu utworzenia <xref:System.Xml.XmlReader> obiektu i zweryfikowania dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat walidacji dokumentów XML przy użyciu <xref:System.Xml.Schema.XmlSchemaSet> , zobacz [Walidacja schematu XML (XSD) z](xml-schema-xsd-validation-with-xmlschemaset.md)zestawem XmlSchemaSet.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [XmlSchemaSet jako pamięć podręczna schematów](xmlschemaset-for-schema-compilation.md)
- [Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md)
