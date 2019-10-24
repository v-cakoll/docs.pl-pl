---
title: Narzędzie definicji schematu XML (Xsd.exe)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 9de4a195f34b0daedcfb3687dbb36495b985092d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775259"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>Narzędzie definicji schematu XML (Xsd.exe)

Narzędzie definicji schematu XML (Xsd.exe) generuje schemat XML lub wspólnej klasy środowiska wykonawczego języka z PLików XDR, XML i XSD lub klasy w zestawie czasu wykonywania.

## <a name="syntax"></a>Składnia

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```

## <a name="argument"></a>Argument

|Argument|Opis|
|--------------|-----------------|
|*plik. rozszerzenie*|Określa PLik wejściowy można przekonwertować. Należy określić rozszerzenie jako jedno z następujących:. XDR,. XML,. xsd,. dll lub. exe.<br /><br /> Jeśli określono PLik schematu XDR (rozszerzenie .xdr), Xsd.exe konwertuje schematu XDR schematu XSD. PLik wyjściowy ma taką samą nazwę schematu XDR, ale z rozszerzeniem xsd.<br /><br /> Jeśli określono PLik XML (rozszerzenie .xml), Xsd.exe wymaga schematu z danych w PLiku i tworzy schematu XSD. PLik wyjściowy ma taką samą nazwę jak PLik XML, ale z rozszerzeniem xsd.<br /><br /> Jeśli określono PLik schematu XML (XSD rozszerzenia), Xsd.exe generuje kod źródłowy środowiska wykonawczego obiektów, które odpowiadają schematu XML.<br /><br /> Jeśli określono PLik zestawu runtime (z rozszerzeniem .exe lub .dll), Xsd.exe generuje schematów dla co najmniej jeden typ w tym zestawie. Można użyć `/type` opcję, aby określić typy, dla których mają być generowanie schematów. Schematy dane wyjściowe są nazywane schema0.xsd, schema1.xsd i tak dalej. XSD. exe tworzy wiele schematów tylko wtedy, gdy podane typy określają przestrzeń nazw przy użyciu `XMLRoot` atrybutu niestandardowego.|

## <a name="general-options"></a>Opcje ogólne

|Opcja|Opis|
|------------|-----------------|
|**/h \[elp \]**|Wyświetla składnię polecenia i opcje narzędzia.|
|**/o \[utputdir \]:** _katalog_|Określa katalog danych dla PLików danych wyjściowych. Ten argument może wystąpić tylko raz. Ustawieniem domyślnym jest bieżący katalog.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|
|**/p \[arameters \]:** _plik. XML_|Opcje dla różnych trybach operacji odczytu z PLiku .xml określony. Krótka forma jest `/p:`. Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .|

## <a name="xsd-file-options"></a>Opcje PLiku XSD
 Należy określić tylko jedną z poniższych opcji dotyczących XSD PLików.

|Opcja|Opis|
|------------|-----------------|
|**/c \[lasses \]**|Generuje klasy, które odpowiadają określony schemat. Aby odczytać dane XML do obiektu, użyj metody <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType>.|
|**/d \[ataset \]**|Generuje klasę pochodną <xref:System.Data.DataSet> , który odpowiada określony schemat. Aby odczytać dane XML w klasie pochodnej, użyj metody <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType>.|

 Można również określić jedną z poniższych opcji dotyczących XSD PLików.

|Opcja|Opis|
|------------|-----------------|
|**/e \[lement \]:** _element_|Określa schemat do generowania kodu dla elementu. Domyślnie wszystkie elementy są wpisane. Tego argumentu można określić więcej niż raz.|
|**/enableDataBinding**|Implementuje interfejs <xref:System.ComponentModel.INotifyPropertyChanged> na wszystkich wygenerowanych typach, aby włączyć powiązanie danych. Krótka forma jest `/edb`.|
|**/enableLinqDataSet**|(Krótka wersja: `/eld`.) Określa, że wygenerowany zestaw danych może być badany przy użyciu LINQ to DataSet. Ta opcja jest stosowana, gdy określona jest również opcja /dataset. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet przegląd](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) i [wykonywanie zapytań dotyczących wpisanych zestawów danych](../../../docs/framework/data/adonet/querying-typed-datasets.md). Aby uzyskać ogólne informacje dotyczące korzystania z LINQ, zobacz [Language-Integrated Query (LINQ C# ) —](../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) — Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).|
|**\[ields/f \]**|Generuje pola, a nie właściwości. Domyślnie są generowane, właściwości.|
|**/l \[anguage \]:** _Język_|Określa język programowania. Wybierz z `CS` (C#, który jest domyślnie), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#). Można również określić w pełni kwalifikowaną nazwę klasy implementującej <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|
|**/n \[amespace \]:** _przestrzeń nazw_|Określa przestrzeń nazw czasu wykonywania wygenerowany typów. Domyślny obszar nazw jest `Schemas`.|
|**/nologo**|Pomija transparentu.|
|**/Order**|Generuje jawne identyfikatory kolejności dla wszystkich elementów członkowskich cząsteczek.|
|**/o \[ut \]:** _katalogname_|Określa katalog wyjściowy, w którym mają zostać umieszczone pliki. Ustawieniem domyślnym jest bieżący katalog.|
|**/u \[ri \]:** _Identyfikator URI_|Określa identyfikator URI dla elementów w schemacie do generowania kodu. Ten identyfikator URI, jeśli istnieje, ma zastosowanie do wszystkich elementów określonych przy użyciu opcji `/element`.|

## <a name="dll-and-exe-file-options"></a>Biblioteka DLL i opcje PLiku EXE

|Opcja|Opis|
|------------|-----------------|
|**/t \[ype \]:** _TypeName_|Określa nazwę typu można utworzyć schemat. Można określić wiele argumentów typu. Jeśli *Właściwość TypeName* nie określa przestrzeni nazw, XSD. exe dopasowuje wszystkie typy w zestawie o określonym typie. Jeśli *Właściwość TypeName* określa przestrzeń nazw, tylko ten typ jest dopasowany. Jeśli parametr *TypeName* jest zakończony znakiem gwiazdki (\*), narzędzie dopasowuje wszystkie typy, które zaczynają się od ciągu poprzedzającego \*. W przypadku pominięcia `/type` opcji Xsd.exe generuje schematów dla wszystkich typów w zestawie.|

## <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono operacje, że Xsd.exe wykonuje.

| | |
|------------|-----------------|
|XDR do XSD|Generuje schematu XML na podstawie PLiku schematu obniżonej danych XML. XDR jest wczesne format schematu oparty na formacie XML.|
|XML do XSD|Generuje schematu XML z PLiku XML.|
|XSD do zestawu danych|Generuje aparatu PLików wykonywalnych języka wspólnego <xref:System.Data.DataSet> klasy z PLiku schematu XSD. Wygenerowany klasy zapewnić model obiektu sformatowanego regularnych danych XML.|
|XSD do klasy|Generuje klasy środowiska wykonawczego na podstawie PLiku schematu XSD. Wygenerowany klasy mogą być używane w połączeniu z <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> do odczytu i zapisu kod XML, który jest zgodna z schemat.|
|Klasy do XSD| Generuje schematu XML na podstawie typ lub typy w PLiku zestawu czasu wykonywania. Wygenerowany schemat definiuje format XML używany przez <xref:System.Xml.Serialization.XmlSerializer>.|

 XSD.exe służy tylko do modyfikowania schematów XML, które podlegają języka definicji schematu XML (XSD) proponowanych przez konsorcjum World Wide Web (W3C). Aby uzyskać więcej informacji na temat propozycji definicji schematu XML lub standardu XML, zobacz <https://w3.org>.

## <a name="setting-options-with-an-xml-file"></a>Ustawianie opcji z PLiku XML

Za pomocą przełącznika `/parameters` można określić pojedynczy plik XML, który ustawia różne opcje. Opcje, które można ustawić zależą od sposobu korzystania z narzędzia XSD.exe. Można także wybrać opcję generowania schematy, generowanie kodu PLików lub generowania kodu PLiki, które zawierają `DataSet` funkcji. Na przykład, można ustawić `<assembly>` elementu na nazwę pliku wykonywalnego (exe) lub biblioteki typów (. dll) podczas generowania schematu, ale nie podczas generowania pliku kodu. Następujące kodu XML przedstawiono sposoby używania `<generateSchemas>` element z określonego PLiku wykonywalnego:

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

Jeśli poprzedni kod XML jest zawarty w pliku o nazwie GenerateSchemas. XML, użyj przełącznika `/parameters`, wpisując następujące polecenie w wierszu polecenia i naciskając klawisz ENTER:

```console
 xsd /p:GenerateSchemas.xml
```

Z drugiej strony jest generowany schematu dla pojedynczego typu znaleziony w zestawie, można użyć następującego kodu XML:

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

Ale aby użyć poprzedzającego kodu, należy również podać nazwę zestawu w wierszu polecenia. Wpisz w wierszu polecenia (przy założeniu, że PLik XML jest o nazwie GenerateSchemaFromType.xml):

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

Należy określić tylko jedną z poniższych opcji dotyczących `<generateSchemas>` elementu.

|Element|Opis|
|-------------|-----------------|
|\<assembly >|Określa generowanie schematu z zestawu.|
|\<type >|Określa typ odnaleźć w zestawie do generowania schemat.|
|\<xml >|Określa PLik XML do generowania schemat.|
|\<xdr >|Określa PLik XDR do generowania schemat.|

Aby wygenerować PLik kodu, należy użyć `<generateClasses>` elementu. Poniższy przykład generuje plik kodu. Należy zauważyć, że dwa atrybuty są także wyświetlane, która pozwala na ustawienie języka programowania i przestrzeni nazw w wygenerowanym PLiku.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 Można ustawić dla opcji `<generateClasses>` obejmują elementu.

|Element|Opis|
|-------------|-----------------|
|\<element >|Określa PLik XSD do generowania kodu dla elementu.|
|\<schemaImporterExtensions >|Określa typ pochodzący od <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> klasy.|
|\<schema >|Określa PLik schematu XML do generowania kodu. Można określić wiele plików schematu XML przy użyciu wielu elementów > \<schema.|

Poniższa tabela zawiera atrybuty, które umożliwia także z `<generateClasses>` elementu.

|Atrybut|Opis|
|---------------|-----------------|
|język|Określa język programowania. Wybierz z `CS` (C#, wartość domyślna), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#). Można również określić w pełni kwalifikowaną nazwę klasy, która implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|— przestrzeń nazw|Określa przestrzeń nazw dla wygenerowanego kodu. Przestrzeń nazw musi być zgodna ze standardami CLR (na przykład bez spacji lub ukośników odwrotnych).|
|opcje|Jedna z następujących wartości: `none`, `properties` (generuje właściwości zamiast pól publicznych), `order` lub `enableDataBinding` (zobacz `/order` i `/enableDataBinding` przełączniki w poprzedniej sekcji opcji pliku XSD.|

 Można także kontrolować sposób `DataSet` kod został wygenerowany za pomocą `<generateDataSet>` elementu. Poniższe XML określa, że wygenerowany kod używa struktur `DataSet` (takich jak Klasa <xref:System.Data.DataTable>) do tworzenia kodu Visual Basic dla określonego elementu. Wygenerowany struktur zestawu danych będzie obsługiwać zapytań LINQ.

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

Można ustawić dla opcji `<generateDataSet>` obejmują elementu.

|Element|Opis|
|-------------|-----------------|
|\<schema >|Określa PLik schematu XML do generowania kodu. Można określić wiele plików schematu XML przy użyciu wielu elementów > \<schema.|

 Poniższa tabela zawiera atrybuty, które mogą być używane z `<generateDataSet>` elementu.

|Atrybut|Opis|
|---------------|-----------------|
|enableLinqDataSet|Określa, że wygenerowanego zestawu danych mogą być wyszukiwane względem przy użyciu LINQ do zestawu danych. Wartość domyślna to false.|
|język|Określa język programowania. Wybierz z `CS` (C#, wartość domyślna), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#). Można również określić w pełni kwalifikowaną nazwę klasy, która implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|— przestrzeń nazw|Określa przestrzeń nazw dla wygenerowanego kodu. Przestrzeń nazw musi być zgodna ze standardami CLR (na przykład bez spacji lub ukośników odwrotnych).|

 Atrybuty, które mogą być ustawione na najwyższym poziomie są `<xsd>` elementu. Te opcje można użyć z żadnego z elementów podrzędnych (`<generateSchemas>`, `<generateClasses>` lub `<generateDataSet>`). Poniższy kod XML generuje kod dla elementu o nazwie "IDItems" w katalogu wyjściowego o nazwie "MyOutputDirectory".

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

Poniższa tabela zawiera atrybuty, które umożliwia także z `<xsd>` elementu.

|Atrybut|Opis|
|---------------|-----------------|
|dane wyjściowe|Nazwa katalogu, w którym zostanie umieszczony wygenerowany plik schematu lub kodu.|
|nologo|Pomija transparentu. Ustaw `true` lub `false`.|
|Pomoc|Wyświetla składnię polecenia i opcje narzędzia. Ustaw `true` lub `false`.|

## <a name="examples"></a>Przykłady
 Następujące polecenie generuje schematu XML z `myFile.xdr` i zapisuje go w bieżącym katalogu.

```console
xsd myFile.xdr
```

Następujące polecenie generuje schematu XML z `myFile.xml` i zapisuje go w określonym katalogu.

```console
xsd myFile.xml /outputdir:myOutputDir
```

Następujące polecenie generuje zestaw danych, który odpowiada określony schemat w języku C# i zapisuje je `XSDSchemaFile.cs` w bieżącym katalogu.

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

Następujące polecenie generuje schematów XML dla wszystkich typów w zestawie `myAssembly.dll` i zapisuje je jako `schema0.xsd` w bieżącym katalogu.

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [Omówienie LINQ to DataSet](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Wykonywanie zapytania do typizowanych zestawów danych](../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [LINQ (zapytanie zintegrowane z językiem)C#()](../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (zapytanie zintegrowane z językiem) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/index.md)
