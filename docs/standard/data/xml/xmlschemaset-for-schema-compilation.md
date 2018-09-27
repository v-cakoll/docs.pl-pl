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
ms.openlocfilehash: c24fe637514ba773cecc7824de276b1707a4e90c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400741"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Klasa XmlSchemaSet na potrzeby kompilacji schematu
W tym artykule opisano <xref:System.Xml.Schema.XmlSchemaSet>, pamięci podręcznej, gdzie schematów języka (XSD) definicji schematu XML mogą być przechowywane i zweryfikowane.  
  
## <a name="the-xmlschemaset-class"></a>Klasa XmlSchemaSet  
 <xref:System.Xml.Schema.XmlSchemaSet> Jest pamięć podręczna, gdzie schematów języka (XSD) definicji schematu XML mogą być przechowywane i zweryfikowane.  
  
 W <xref:System.Xml?displayProperty=nameWithType> wersji 1.0 schematów XML zostały załadowane do <xref:System.Xml.Schema.XmlSchemaCollection> klasy jako biblioteki schematów. W <xref:System.Xml?displayProperty=nameWithType> w wersji 2.0, <xref:System.Xml.XmlValidatingReader> i <xref:System.Xml.Schema.XmlSchemaCollection> klasy są przestarzałe i zostały zastąpione przez <xref:System.Xml.XmlReader.Create%2A> metod i <xref:System.Xml.Schema.XmlSchemaSet> klasy odpowiednio.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Wprowadzono rozwiązać wiele problemów, takich jak zgodność standardów, wydajność i przestarzały format schematu Microsoft-danych XML (XDR).  
  
 Poniżej przedstawiono porównanie <xref:System.Xml.Schema.XmlSchemaCollection> klasy i <xref:System.Xml.Schema.XmlSchemaSet> klasy.  
  
|Użyciu klasy XmlSchemaCollection|Element XmlSchemaSet|  
|-------------------------|------------------|  
|Obsługuje XDR firmy Microsoft i W3C schematów XML.|Obsługuje tylko schematów W3C XML.|  
|Schematy są kompilowane podczas <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metoda jest wywoływana.|Schematy nie są kompilowane podczas <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda jest wywoływana. Zapewnia to zwiększenie wydajności podczas tworzenia biblioteki schematów.|  
|Każdym ze schematów generuje poszczególnych skompilowanych wersji, która może spowodować "Wyspy schematu." Co w efekcie obejmuje wszystkie i Importy są ograniczone tylko w tym schemacie.|Skompilowanych schematów Wygeneruj jeden schemat logiczne, "set" schematów. Importowane schematy w schemacie, które są dodawane do zestawu są bezpośrednio dodać do zbioru samodzielnie. Oznacza to, że wszystkie typy są dostępne dla wszystkich schematów.|  
|Tylko jeden schemat dla określonego docelowego obszaru nazw może znajdować się w kolekcji.|Tak długo, jak to zapobiec konfliktom typu można dodać wiele schematów dla tej samej docelowego obszaru nazw.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrowanie do element XmlSchemaSet  
 Poniższy przykład kodu Przewodnik po migracji do nowego <xref:System.Xml.Schema.XmlSchemaSet> przestarzałe klasy <xref:System.Xml.Schema.XmlSchemaCollection> klasy. Przykładowy kod przedstawia następujące główne różnice między dwoma klasami.  
  
-   W odróżnieniu od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy nie są kompilowane podczas wywoływania <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metody <xref:System.Xml.Schema.XmlSchemaSet> zostanie jawnie wywołany w przykładowym kodzie.  
  
-   Iterowanie <xref:System.Xml.Schema.XmlSchemaSet>, należy użyć <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Oto przestarzała <xref:System.Xml.Schema.XmlSchemaCollection> przykładowy kod.  
  
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
  
 Poniżej przedstawiono odpowiednik <xref:System.Xml.Schema.XmlSchemaSet> przykładowy kod.  
  
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
 Schematy są dodawane do <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. Po dodaniu do schematu <xref:System.Xml.Schema.XmlSchemaSet>, jest on skojarzony z docelowej przestrzeni nazw identyfikatora URI. Docelowy obszar nazw, albo można określić identyfikatora URI jako parametr do <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody lub jeśli nie docelowego obszaru nazw jest określony, <xref:System.Xml.Schema.XmlSchemaSet> korzysta z docelowego obszaru nazw, zdefiniowanej w schemacie.  
  
 Schematy są pobierane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaSet> umożliwia iteracyjne przeglądanie <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Albo zwraca wartość właściwości wszystkich <xref:System.Xml.Schema.XmlSchema> obiektów zawartych w <xref:System.Xml.Schema.XmlSchemaSet>, lub podany docelowego obszaru nazw parametrów, zwraca wszystkie <xref:System.Xml.Schema.XmlSchema> obiektów, które należą do docelowego obszaru nazw. Jeśli `null` jest określony jako parametr przestrzeni nazw docelowy <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość zwraca wszystkie schematy bez przestrzeni nazw.  
  
 W poniższym przykładzie dodano `books.xsd` schemat `http://www.contoso.com/books` przestrzeń nazw <xref:System.Xml.Schema.XmlSchemaSet>, umożliwia pobranie wszystkich schematów, które należą do `http://www.contoso.com/books` przestrzeni nazw z <xref:System.Xml.Schema.XmlSchemaSet>, a następnie zapisuje te schematy do <xref:System.Console>.  
  
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
  
 Aby uzyskać więcej informacji na temat dodawania i pobierania schematów na podstawie <xref:System.Xml.Schema.XmlSchemaSet> obiektu, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody i <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Dokumentacja referencyjna właściwość.  
  
## <a name="compiling-schemas"></a>Kompilowania schematów  
 Schematy w <xref:System.Xml.Schema.XmlSchemaSet> są kompilowane do jednego schematu logicznego przez <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
>  W przeciwieństwie do przestarzałe <xref:System.Xml.Schema.XmlSchemaCollection> klasy, schematy nie są kompilowane podczas <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda jest wywoływana.  
  
 Jeśli <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda wykonuje z powodzeniem, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> ustawiono `true`.  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Właściwość nie ma wpływu Jeśli schematy są edytowane while w <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizacje schematów poszczególnych <xref:System.Xml.Schema.XmlSchemaSet> nie są śledzone. W rezultacie <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość może być `true` nawet jednego ze schematów zawartych w <xref:System.Xml.Schema.XmlSchemaSet> zostanie zmieniony, tak długo, jak schematy nie zostały dodane lub usunięte z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 W poniższym przykładzie dodano `books.xsd` plik <xref:System.Xml.Schema.XmlSchemaSet> , a następnie wywołuje <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody.  
  
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
  
 Aby uzyskać więcej informacji na temat kompilowania schematów w <xref:System.Xml.Schema.XmlSchemaSet>, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda dokumentacji.  
  
## <a name="reprocessing-schemas"></a>Ponowne przetwarzanie schematów  
 Ponowne przetwarzanie schematu w <xref:System.Xml.Schema.XmlSchemaSet> wykonuje przetwarzania wstępnego czynności wykonywane na schemacie podczas <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana. Jeśli wywołanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda zakończy się pomyślnie, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> ustawiono `false`.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Metoda powinna być używana, gdy schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany po <xref:System.Xml.Schema.XmlSchemaSet> wykonał kompilację.  
  
 W poniższym przykładzie pokazano ponownego przetworzenia dodane do schematu <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody. Po <xref:System.Xml.Schema.XmlSchemaSet> jest skompilowana przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda i schemat dodany do <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość jest ustawiona na `true` nawet wtedy, gdy schemat w <xref:System.Xml.Schema.XmlSchemaSet> został zmodyfikowany. Wywoływanie <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda wykonuje wszystkie wstępnego przetwarzania wykonywane przez <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody i zestawy <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> właściwość `false`.  
  
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
  
 Aby uzyskać więcej informacji na temat ponownego przetworzenia schemat w <xref:System.Xml.Schema.XmlSchemaSet>, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda dokumentacji.  
  
## <a name="checking-for-a-schema"></a>Sprawdzanie, czy schemat  
 Możesz użyć <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> do sprawdzenia, jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda przyjmuje albo docelowej przestrzeni nazw lub <xref:System.Xml.Schema.XmlSchema> obiektu do wyszukania. W obu przypadkach <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda zwraca `true` Jeśli schemat jest zawarty w <xref:System.Xml.Schema.XmlSchemaSet>; w przeciwnym razie zwraca `false`.  
  
 Aby uzyskać więcej informacji na temat sprawdzania pod kątem schematu zobacz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda dokumentacji.  
  
## <a name="removing-schemas"></a>Usuwanie schematów  
 Schematy są usuwane z <xref:System.Xml.Schema.XmlSchemaSet> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda usuwa określony schemat z <xref:System.Xml.Schema.XmlSchemaSet>, podczas gdy <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda usuwa określony schemat i wszystkich schematów importuje z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 W poniższym przykładzie pokazano wiele schematów do dodawania <xref:System.Xml.Schema.XmlSchemaSet>, a następnie użyć <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metodę, aby usunąć jedną ze schematów i wszystkich schematów importuje.  
  
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
  
 Aby uzyskać więcej informacji o usuwaniu schematów na podstawie <xref:System.Xml.Schema.XmlSchemaSet>, zobacz <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> i <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody dokumentacji.  
  
## <a name="schema-resolution-and-xsimport"></a>Rozdzielczość schematu i xs:import  
 Poniższe przykłady przedstawiają <xref:System.Xml.Schema.XmlSchemaSet> zachowania w przypadku importowania schematów, gdy istnieje wiele schematów dla danego obszaru nazw, w <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Na przykład, rozważmy <xref:System.Xml.Schema.XmlSchemaSet> zawierający wiele schematów dla `http://www.contoso.com` przestrzeni nazw. Schemat z następującymi `xs:import` dyrektywy zostanie dodany do <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Próbuje zaimportować schematu dla `http://www.contoso.com` przestrzeni nazw przez załadowanie go z `http://www.contoso.com/schema.xsd` adresu URL. Deklaracja schematu i typów zadeklarowane w dokumencie schematu dostępne są wyłącznie w schemacie importowania, nawet jeśli ma innych dokumentów schematu dla `http://www.contoso.com` przestrzeni nazw w <xref:System.Xml.Schema.XmlSchemaSet>. Jeśli `schema.xsd` nie można znaleźć w pliku `http://www.contoso.com/schema.xsd` adresu URL, Brak schematu dla `http://www.contoso.com` przestrzeni nazw jest importowany do importowania schematu.  
  
## <a name="validating-xml-documents"></a>Walidacja dokumentów XML  
 Dokumenty XML mogą być weryfikowany pod kątem schematów w <xref:System.Xml.Schema.XmlSchemaSet>. Sprawdź poprawność dokumentu XML, dodając schematu <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu lub poprzez dodanie <xref:System.Xml.Schema.XmlSchemaSet> do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> obiektu. <xref:System.Xml.XmlReaderSettings> Obiekt jest następnie używany przez <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy w celu utworzenia <xref:System.Xml.XmlReader> obiektu i sprawdź poprawność dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat sprawdzania poprawności XML dokumenty przy użyciu <xref:System.Xml.Schema.XmlSchemaSet>, zobacz [walidacji schematu XML (XSD) przy użyciu klasy XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
- [Element XmlSchemaSet jako pamięci podręcznej schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Sprawdzanie poprawności schematu XML (XSD) przy użyciu klasy XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
