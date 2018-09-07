---
title: Narzędzie definicji schematu XML (Xsd.exe)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: a3a16e92dab6994de6bfa99c248ff0b13658e22d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079750"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>Narzędzie definicji schematu XML (Xsd.exe)
Narzędzie definicji schematu XML (Xsd.exe) generuje schemat XML lub wspólnej klasy środowiska wykonawczego języka z PLików XDR, XML i XSD lub klasy w zestawie czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Opis|  
|--------------|-----------------|  
|*file.extension*|Określa PLik wejściowy można przekonwertować. Należy określić extensionas, jedną z następujących: .xdr, XML, XSD, .dll lub .exe.<br /><br /> Jeśli określono PLik schematu XDR (rozszerzenie .xdr), Xsd.exe konwertuje schematu XDR schematu XSD. PLik wyjściowy ma taką samą nazwę schematu XDR, ale z rozszerzeniem xsd.<br /><br /> Jeśli określono PLik XML (rozszerzenie .xml), Xsd.exe wymaga schematu z danych w PLiku i tworzy schematu XSD. PLik wyjściowy ma taką samą nazwę jak PLik XML, ale z rozszerzeniem xsd.<br /><br /> Jeśli określono PLik schematu XML (XSD rozszerzenia), Xsd.exe generuje kod źródłowy środowiska wykonawczego obiektów, które odpowiadają schematu XML.<br /><br /> Jeśli określono PLik zestawu runtime (z rozszerzeniem .exe lub .dll), Xsd.exe generuje schematów dla co najmniej jeden typ w tym zestawie. Można użyć `/type` opcję, aby określić typy, dla których mają być generowanie schematów. Schematy dane wyjściowe są nazywane schema0.xsd, schema1.xsd i tak dalej. XSD.exe tworzy wiele schematów tylko wtedy, gdy w danym typami określić za pomocą nazw `XMLRoot` atrybutu niestandardowego.|  
  
## <a name="general-options"></a>Opcje ogólne  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/o**[**utputdir**] **: *** katalogu*|Określa katalog danych dla PLików danych wyjściowych. Ten argument może wystąpić tylko raz. Ustawieniem domyślnym jest bieżący katalog.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/P [arameters]:** *file.xml*|Opcje dla różnych trybach operacji odczytu z PLiku .xml określony. Formularz Skrócony jest "/ p:". Aby uzyskać więcej informacji zobacz następujące sekcji uwag.|  
  
## <a name="xsd-file-options"></a>Opcje PLiku XSD  
 Należy określić tylko jedną z poniższych opcji dotyczących XSD PLików.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/c**[**lasses**]|Generuje klasy, które odpowiadają określony schemat. Do odczytywania danych XML do obiektu, użyj `System.Xml.Serialization.XmlSerializer.Deserializer` metody.|  
|**/d**[**ataset**]|Generuje klasę pochodną <xref:System.Data.DataSet> , który odpowiada określony schemat. Do odczytywania danych XML w klasie pochodnej, użyj `System.Data.DataSet.ReadXml` metody.|  
  
 Można również określić jedną z poniższych opcji dotyczących XSD PLików.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/e**[**lementuj**] **: *** — element*|Określa schemat do generowania kodu dla elementu. Domyślnie wszystkie elementy są wpisane. Tego argumentu można określić więcej niż raz.|  
|**/enableDataBinding**|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu dla wszystkich typów wygenerowanego umożliwiające powiązanie danych. Formularz Skrócony jest `/edb`.|  
|**/enableLinqDataSet**|(Skrócona forma: `/eld`.) Określa, że wygenerowanego zestawu danych mogą być wyszukiwane względem przy użyciu LINQ do zestawu danych. Ta opcja jest stosowana, gdy określona jest również opcja /dataset. Aby uzyskać więcej informacji, zobacz [omówienie LINQ to DataSet](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) i [zapytań wpisanych zestawów danych](../../../docs/framework/data/adonet/querying-typed-datasets.md). Aby uzyskać ogólne informacje o korzystaniu z LINQ, zobacz [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).|  
|**/f**[**ields**]|Generuje pola, a nie właściwości. Domyślnie są generowane, właściwości.|  
|**/l**[**język**] **: *** języka*|Określa język programowania. Wybierz z `CS` (C#, który jest domyślnie), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#). Można również określić w pełni kwalifikowaną nazwę klasy wykonania <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|  
|**/n**[**amespace**] **: *** przestrzeni nazw*|Określa przestrzeń nazw czasu wykonywania wygenerowany typów. Domyślny obszar nazw jest `Schemas`.|  
|**/nologo**|Pomija transparentu.|  
|**/ ORDER**|Generuje jawnego kolejności identyfikatorów dla wszystkich członków cząstek.|  
|**/o [ut]:** *directoryName*|Określa katalog danych wyjściowych do umieszczenia plików w. Ustawieniem domyślnym jest bieżący katalog.|  
|**/u**[**wystąpień zarezerwowanych**] **: *** identyfikatora uri*|Określa identyfikator URI dla elementów w schemacie do generowania kodu. Ten identyfikator URI, jeśli jest obecny, ma zastosowanie do wszystkich elementów określony za pomocą `/element` opcji.|  
  
## <a name="dll-and-exe-file-options"></a>Biblioteka DLL i opcje PLiku EXE  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/t**[**yp**] **: *** typename*|Określa nazwę typu można utworzyć schemat. Można określić wiele argumentów typu. Jeśli *typename* nie określa obszar nazw dopasowań Xsd.exe wszystkie typy w zestawie z określonym typem. Jeśli *typename* określa obszar nazw, tylko dopasowaniu typu. Jeśli *typename* kończy się znakiem gwiazdki (\*), to narzędzie jest zgodna wszystkich typów, które zaczyna się od ciągu poprzedniego \*. W przypadku pominięcia `/type` opcji Xsd.exe generuje schematów dla wszystkich typów w zestawie.|  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono operacje, że Xsd.exe wykonuje.  
  
 XDR do XSD  
 Generuje schematu XML na podstawie PLiku schematu obniżonej danych XML. XDR jest wczesne format schematu oparty na formacie XML.  
  
 XML do XSD  
 Generuje schematu XML z PLiku XML.  
  
 XSD do zestawu danych  
 Generuje aparatu PLików wykonywalnych języka wspólnego <xref:System.Data.DataSet> klasy z PLiku schematu XSD. Wygenerowany klasy zapewnić model obiektu sformatowanego regularnych danych XML.  
  
 XSD do klasy  
 Generuje klasy środowiska wykonawczego na podstawie PLiku schematu XSD. Wygenerowany klasy mogą być używane w połączeniu z <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> do odczytu i zapisu kod XML, który jest zgodna z schemat.  
  
 Klasy do XSD  
 Generuje schematu XML na podstawie typ lub typy w PLiku zestawu czasu wykonywania. Wygenerowany schemat definiuje format XML używany przez `System.Xml.Serialization.XmlSerializer`.  
  
 XSD.exe służy tylko do modyfikowania schematów XML, które podlegają języka definicji schematu XML (XSD) proponowanych przez konsorcjum World Wide Web (W3C). Aby uzyskać więcej informacji na propozycję definicji schematu XML lub standardu XML zobacz http://w3.org.  
  
## <a name="setting-options-with-an-xml-file"></a>Ustawianie opcji z PLiku XML  
 Za pomocą `/parameters` przełącznika, można określić pojedynczy plik XML, który ustawia różne opcje. Opcje, które można ustawić zależą od sposobu korzystania z narzędzia XSD.exe. Można także wybrać opcję generowania schematy, generowanie kodu PLików lub generowania kodu PLiki, które zawierają `DataSet` funkcji. Na przykład można ustawić `<assembly\>` element na nazwę pliku wykonywalnego (.exe) lub wpisz biblioteki (.dll) pliku podczas generowania schematu, ale nie w momencie generowania pliku kodu. Następujące kodu XML przedstawiono sposoby używania `<generateSchemas\>` element z określonego PLiku wykonywalnego:  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 Jeśli poprzedni kod XML znajduje się w pliku o nazwie GenerateSchemas.xml, należy użyć `/parameters` Przełącz wpisując następujące polecenie w wierszu polecenia i naciskając klawisz ENTER:  
  
 `xsd /p:GenerateSchemas.xml`  
  
 Z drugiej strony jest generowany schematu dla pojedynczego typu znaleziony w zestawie, można użyć następującego kodu XML:  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 Jednak aby użyć poprzedniego kodu, należy również podać nazwę zestawu, w tym celu w wierszu polecenia. Wpisz w wierszu polecenia (przy założeniu, że PLik XML jest o nazwie GenerateSchemaFromType.xml):  
  
 `xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe`  
  
 Należy określić tylko jedną z poniższych opcji dotyczących `\<generateSchemas>` elementu.  
  
|Element|Opis|  
|-------------|-----------------|  
|\<Zestaw >|Określa generowanie schematu z zestawu.|  
|\<Typ >|Określa typ odnaleźć w zestawie do generowania schemat.|  
|\<xml>|Określa PLik XML do generowania schemat.|  
|\<xdr>|Określa PLik XDR do generowania schemat.|  
  
 Aby wygenerować PLik kodu, należy użyć `<generateClasses\>` elementu. Poniższy przykład generuje plik kodu. Należy zauważyć, że dwa atrybuty są także wyświetlane, która pozwala na ustawienie języka programowania i przestrzeni nazw w wygenerowanym PLiku.  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 Można ustawić dla opcji `\<generateClasses>` obejmują elementu.  
  
|Element|Opis|  
|-------------|-----------------|  
|\<Element >|Określa PLik XSD do generowania kodu dla elementu.|  
|\<schemaImporterExtensions>|Określa typ pochodzący od <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> klasy.|  
|\<schema>|Określa PLik schematu XML do generowania kodu.  Wiele plików schematów XML można określić za pomocą wielu \<schematu > elementy.|  
  
 Poniższa tabela zawiera atrybuty, które umożliwia także z `<generateClasses\>` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|język|Określa język programowania. Wybierz z `CS` (C#, wartość domyślna), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#). Można również określić w pełni kwalifikowaną nazwę klasy, która implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.|  
|— przestrzeń nazw|Określa przestrzeń nazw dla wygenerowanego kodu. Przestrzeń nazw musi być zgodna ze standardami CLR (na przykład, bez spacji i znaków ukośnika odwrotnego).|  
|opcje|Jedną z następujących wartości: `none`, `properties` (generuje właściwości zamiast pola publiczne), `order`, lub `enableDataBinding` (zobacz `/order` i `/enableDataBinding` przełączniki w poprzedniej sekcji Opcje pliku XSD.|  
  
 Można także kontrolować sposób `DataSet` kod został wygenerowany za pomocą `<generateDataSets\>` elementu. Następujący kod XML określa, że wygenerowany codeuses `DataSet` struktur (takie jak <xref:System.Data.DataTable> klasy) do tworzenia kodu języka Visual Basic dla określonego elementu. Wygenerowany struktur zestawu danych będzie obsługiwać zapytań LINQ.  
  
 `<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>`  
  
 `<generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>`  
  
 `</generateDataSet>`  
  
 `</xsd>`  
  
 Można ustawić dla opcji `<generateDataSet\>` obejmują elementu.  
  
|Element|Opis|  
|-------------|-----------------|  
|\<schema>|Określa PLik schematu XML do generowania kodu. Wiele plików schematów XML można określić za pomocą wielu \<schematu > elementy.|  
  
 Poniższa tabela zawiera atrybuty, które mogą być używane z `<generateDataSet\>` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|enableLinqDataSet|Określa, że wygenerowanego zestawu danych mogą być wyszukiwane względem przy użyciu LINQ do zestawu danych. Wartość domyślna to false.|  
|język|Określa język programowania. Wybierz z `CS` (C#, wartość domyślna), `VB` (Visual Basic), `JS` (JScript) lub `VJS` (Visual J#). Można również określić w pełni kwalifikowaną nazwę klasy, która implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.|  
|— przestrzeń nazw|Określa przestrzeń nazw dla wygenerowanego kodu. Przestrzeń nazw musi być zgodna ze standardami CLR (na przykład, bez spacji i znaków ukośnika odwrotnego).|  
  
 Atrybuty, które mogą być ustawione na najwyższym poziomie są `<xsd\>` elementu. Te opcje można użyć z żadnego z elementów podrzędnych (`<generateSchemas\>`, `<generateClasses\>` lub `<generateDataSet\>`). Poniższy kod XML generuje kod dla elementu o nazwie "IDItems" w katalogu wyjściowego o nazwie "MyOutputDirectory".  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
<element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 Poniższa tabela zawiera atrybuty, które umożliwia także z `\<xsd>` elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|dane wyjściowe|Nazwa katalogu, w którym zostaną umieszczone wygenerowany plik schematu lub kod.|  
|nologo|Pomija transparentu. Ustaw `true` lub `false`.|  
|Pomoc|Wyświetla składnię polecenia i opcje narzędzia. Ustaw `true` lub `false`.|  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje schematu XML z `myFile.xdr` i zapisuje go w bieżącym katalogu.  
  
```  
xsd myFile.xdr   
```  
  
 Następujące polecenie generuje schematu XML z `myFile.xml` i zapisuje go w określonym katalogu.  
  
```  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 Następujące polecenie generuje zestaw danych, który odpowiada określony schemat w języku C# i zapisuje je `XSDSchemaFile.cs` w bieżącym katalogu.  
  
```  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 Następujące polecenie generuje schematów XML dla wszystkich typów w zestawie `myAssembly.dll` i zapisuje je jako `schema0.xsd` w bieżącym katalogu.  
  
```  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet>  
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>  
- [Narzędzia](../../../docs/framework/tools/index.md)      
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
- [Omówienie LINQ to DataSet](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
- [Wykonywanie zapytania do typizowanych zestawów danych](../../../docs/framework/data/adonet/querying-typed-datasets.md)  
- [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
