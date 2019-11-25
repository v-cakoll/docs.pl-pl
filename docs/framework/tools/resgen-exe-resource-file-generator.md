---
title: Resgen.exe (Generator pliku zasobów)
ms.date: 03/30/2017
helpviewer_keywords:
- resource files, .resources files
- resource files, .resx files
- resx files (resource files)
- .resources files
- files, converting
- Resource File Generator
- .resx files
- Resgen.exe
- resource files, converting
- converting files, Resource File Generator
- binary resources files
- embedding files in runtime binary executable
ms.assetid: 8ef159de-b660-4bec-9213-c3fbc4d1c6f4
ms.openlocfilehash: 5fc2bcb03ae6814d69e229ba083c1d5c44ae8ff3
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204616"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Generator pliku zasobów)
Generator plików zasobów (Resgen.exe) konwertuje pliki tekstowe (txt lub restext) i pliki zasobów w formacie XML (resx) na pliki binarne (resources) środowiska uruchomieniowego języka wspólnego, które można osadzić w binarnym pliku wykonywalnym środowiska uruchomieniowego lub zestawie satelickim. (See [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).)  
  
 Program Resgen.exe to uniwersalne narzędzie do konwersji zasobów, które wykonuje następujące zadania:  
  
- Konwertuje pliki txt lub restext na pliki resx lub resources. (Format plików restext jest identyczny z formatem plików txt. Jednak rozszerzenie restext pomaga łatwiej zidentyfikować pliki tekstowe, które zawierają definicje zasobów).  
  
- Konwertuje pliki resources na pliki tekstowe lub resx.  
  
- Konwertuje pliki resx na pliki tekstowe lub resources.  
  
- Extracts the string resources from an assembly into a .resw file that is suitable for use in a Windows 8.x Store app.  
  
- Creates a strongly typed class that provides access to individual named resources and to the <xref:System.Resources.ResourceManager> instance.  
  
 Jeśli działanie programu Resgen.exe kończy się niepowodzeniem z dowolnej przyczyny, zwracaną wartością jest -1.  
  
 To get help with Resgen.exe, you can use the following command, with no options specified, to display the command syntax and options for Resgen.exe:  
  
```console  
resgen  
```  
  
 You can also use the `/?` switch:  
  
```console  
resgen /?  
```  
  
 If you use Resgen.exe to generate binary .resources files, you can use a language compiler to embed the binary files into executable assemblies, or you can use the [Assembly Linker (Al.exe)](al-exe-assembly-linker.md) to compile them into satellite assemblies.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
resgen  [-define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr lub opcja|Opis|  
|-------------------------|-----------------|  
|`/define:` *symbol1*[, *symbol2*,...]|Starting with the .NET Framework 4.5, supports conditional compilation in text-based (.txt or .restext) resource files. If *symbol* corresponds to a symbol included in the input text file within a `#ifdef` construct, the associated string resource is included in the .resources file. If the input text file includes an `#if !` statement with a symbol that is not defined by the `/define` switch, the associated string resource is included in the resources file.<br /><br /> `/define` is ignored if it is used with non-text files. W symbolach jest uwzględniania wielkość liter.<br /><br /> For more information about this option, see [Conditionally Compiling Resources](#Conditional) later in this topic.|  
|`useSourcePath`|Określa, że bieżący katalog pliku wejściowego ma być używany na potrzeby rozpoznawania względnych ścieżek plików.|  
|`/compile`|Umożliwia określenie wielu plików tekstowych lub resx w celu konwersji na wiele plików resources w pojedynczej zbiorczej operacji. Jeśli ta opcja nie jest określona, można określić tylko jeden argument pliku wejściowego. Output files are named *filename*.resources.<br /><br /> This option cannot be used with the `/str:` option.<br /><br /> For more information about this option, see [Compiling or Converting Multiple Files](#Multiple) later in this topic.|  
|`/r:``assembly`|Odwołuje się do metadanych z określonego zestawu. Jest używana podczas konwersji plików resx i zezwala programowi Resgen.exe na serializację lub deserializację zasobów obiektu. It is similar to the `/reference:` or `/r:` options for the C# and Visual Basic compilers.|  
|`filename.extension`|Określa nazwę pliku wejściowego do konwersji. If you're using the first, lengthier command-line syntax presented before this table,  `extension` must be one of the following:<br /><br /> .txt lub .restext<br /> Plik tekstowy do konwersji na plik resources lub resx. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów. For information about the file format, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Plik zasobów w języku XML do konwersji na plik .resources lub plik tekstowy (txt lub restext).<br /><br /> .resources<br /> Plik binarny zasobów do konwersji na plik resx lub plik tekstowy (txt lub restext).<br /><br /> If you're using the second, shorter command-line syntax presented before this table, `extension` must be the following:<br /><br /> .exe lub .dll<br /> A .NET Framework assembly (executable or library) whose string resources are to be extracted to a .resw file for use in developing Windows 8.x Store apps.|  
|`outputFilename.extension`|Określa nazwę i typ tworzonego pliku zasobów.<br /><br /> Ten argument jest opcjonalny podczas konwersji z pliku txt, restext lub resx na plik resources. If you do not specify `outputFilename`, Resgen.exe appends a .resources extension to the input `filename` and writes the file to the directory that contains `filename,extension`.<br /><br /> The `outputFilename.extension` argument is mandatory when converting from a .resources file. Określa nazwę pliku z rozszerzeniem resx podczas konwersji pliku resources na plik zasobów w formacie XML. Określa nazwę pliku z rozszerzeniem txt lub restext podczas konwersji na plik resources lub plik tekstowy. Plik resources należy konwertować na plik txt tylko wtedy, gdy plik resources zawiera wyłącznie wartości w postaci ciągów.|  
|`outputDirectory`|For Windows 8.x Store apps, specifies the directory in which a .resw file that contains the string resources in `filename.extension` will be written. `outputDirectory` must already exist.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Creates a strongly typed resource class file in the programming language specified in the `language` option. `language` can consist of one of the following literals:<br /><br /> -   For C#: `c#`, `cs`, or `csharp`.<br />-   For Visual Basic: `vb` or `visualbasic`.<br />-   For VBScript: `vbs` or `vbscript`.<br />-   For C++: `c++`, `mc`, or `cpp`.<br />-   For JavaScript: `js`, `jscript`, or `javascript`.<br /><br /> The `namespace` option specifies the project's default namespace, the `classname` option specifies the name of the generated class, and the `filename` option specifies the name of the class file.<br /><br /> The `/str:` option allows only one input file, so it cannot be used with the `/compile` option.<br /><br /> If `namespace` is specified but `classname` is not, the class name is derived from the output file name (for example, underscores are substituted for periods). Zasoby silnie typizowane mogą nie działać poprawnie jako wynik. Aby tego uniknąć, należy określić zarówno nazwę klasy, jak i nazwę pliku wyjściowego.<br /><br /> For more information about this option, see [Generating a Strongly Typed Resource Class](#Strong) later in this topic.|  
|`/publicClass`|Tworzy silnie typizowaną klasę zasobu jako klasę publiczną. By default, the resource class is `internal` in C# and `Friend` in Visual Basic.<br /><br /> This option is ignored if the `/str:` option is not used.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Program Resgen.exe i typy plików zasobów  
 Aby program Resgen.exe mógł pomyślnie konwertować zasoby, pliki tekstowe i resx muszą mieć poprawny format.  
  
### <a name="text-txt-and-restext-files"></a>Pliki tekstowe (txt i restext)  
 Pliki tekstowe (txt lub restext) mogą zawierać tylko zasoby w postaci ciągów. Zasoby w postaci ciągów są przydatne podczas pisania aplikacji, która musi być przetłumaczona na kilka języków. Na przykład można łatwo poddać regionalizacji napisy w menu przy użyciu odpowiedniego zasobu w postaci ciągu. Program Resgen.exe odczytuje pliki tekstowe, które zawierają pary nazwa/wartość, gdzie nazwa jest ciągiem opisującym zasób, a wartość to właśnie ciąg zasobu.  
  
> [!NOTE]
> For information about the format of .txt and .restext files, see the "Resources in Text Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Plik tekstowy, który zawiera zasoby, musi być zapisany z użyciem kodowania UTF-8 lub Unicode (UTF-16), chyba że zawiera tylko znaki z zakresu Łaciński podstawowy (do U+007F). Program Resgen.exe usuwa rozszerzone znaki ANSI podczas przetwarzania pliku tekstowego, który został zapisany przy użyciu kodowania ANSI.  
  
 Program Resgen.exe sprawdza, czy plik tekstowy zawiera zduplikowane nazwy zasobów. Jeśli plik tekstowy zawiera zduplikowane nazwy zasobów, program Resgen.exe wyświetli ostrzeżenie i zignoruje drugą wartość.  
  
### <a name="resx-files"></a>Pliki resx  
 Format plików zasobów resx składa się z wpisów XML. Można określić zasoby w postaci ciągów w tych wpisach XML, tak jak w plikach tekstowych. Główną zaletą plików resx w porównaniu z plikami tekstowymi jest to, że można określić lub osadzić w nich obiekty. Podczas przeglądania pliku resx można zobaczyć binarną formę osadzonego obiektu (na przykład obrazka), gdy te informacje binarne są częścią manifestu zasobu. Tak jak w przypadku plików tekstowych, plik resx można otworzyć za pomocą edytora tekstów (takiego jak Notatnik lub program Microsoft Word), a następnie można pisać i analizować jego zawartość, a także wykonywać na niej różne operacje. Należy zauważyć, że wymaga to dobrej znajomości tagów XML i struktury pliku resx. For more details on the .resx file format, see the "Resources in .resx Files" section of [Creating Resource Files](../resources/creating-resource-files-for-desktop-apps.md).  
  
 In order to create a .resources file that contains embedded nonstring objects, you must either use Resgen.exe to convert a .resx file containing objects or add the object resources to your file directly from code by calling the methods provided by the <xref:System.Resources.ResourceWriter> class.  
  
 Jeśli plik resx lub resources zawiera obiekty i zostanie użyty program Resgen.exe w celu przekonwertowania go na plik tekstowy, wszystkie zasoby w postaci ciągów zostaną przekonwertowane poprawnie, ale typy danych obiektów niebędących ciągami również zostaną zapisane w pliku jako ciągi. W wyniku konwersji obiekty osadzone zostaną utracone, a program Resgen.exe zgłosi, że wystąpił błąd podczas pobierania zasobów.  
  
### <a name="converting-between-resources-file-types"></a>Konwertowanie między typami plików zasobów  
 Podczas konwertowania między różnymi typami plików zasobów program Resgen.exe może nie być w stanie dokonać konwersji lub może spowodować utratę informacji o określonych zasobach, w zależności od typu plików źródłowego i docelowego. W poniższej tabeli określono typy konwersji, które kończą się sukcesem w przypadku konwertowania z jednego typu pliku zasobów na inny.  
  
|Konwersja z|Na plik tekstowy|Na plik resx|Na plik resw|Na plik resources|  
|------------------|------------------|-------------------|-------------------|------------------------|  
|Plik tekstowy (txt lub restext)|--|Brak problemów|Nieobsługiwane|Brak problemów|  
|Plik resx|Konwersja nie powiedzie się, jeżeli plik zawiera zasoby, które nie są ciągami (w tym łącza do plików)|--|Nieobsługiwane|Brak problemów|  
|Plik resources|Konwersja nie powiedzie się, jeżeli plik zawiera zasoby, które nie są ciągami (w tym łącza do plików)|Brak problemów|Nieobsługiwane|--|  
|Zestaw exe lub dll|Nieobsługiwane|Nieobsługiwane|Tylko zasoby w postaci ciągów (w tym nazwy ścieżek) są rozpoznawane jako zasoby|Nieobsługiwane|  
  
## <a name="performing-specific-resgenexe-tasks"></a>Wykonywanie określonych zadań w programie Resgen.exe  
 You can use Resgen.exe in diverse ways: to compile a text-based or XML-based resource file into a binary file, to convert between resource file formats, and to generate a class that wraps <xref:System.Resources.ResourceManager> functionality and provides access to resources. Ta sekcja zawiera szczegółowe informacje dotyczące każdego zadania:  
  
- [Compiling Resources into a Binary File](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Converting Between Resource File Types](resgen-exe-resource-file-generator.md#Convert)  
  
- [Compiling or Converting Multiple Files](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Exporting Resources to a .resw File](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Conditionally Compiling Resources](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generating a Strongly Typed Resource Class](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilowanie zasobów do pliku binarnego  
 Najbardziej powszechnym zastosowaniem programu Resgen.exe jest kompilacja pliku zasobów w formacie tekstowym (pliku txt lub restext) lub w formacie XML (pliku resx) do pliku binarnego resources. The output file then can be embedded in a main assembly by a language compiler or in a satellite assembly by [Assembly Linker (AL.exe)](al-exe-assembly-linker.md).  
  
 Składnia służąca do kompilacji pliku zasobów jest następująca:  
  
```console  
resgen inputFilename [outputFilename]   
```  
  
 gdzie parametrami są:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, który należy skompilować. Program Resgen.exe kompiluje tylko pliki z rozszerzeniem txt, restext lub resx.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`. If `outputFilename` includes a directory path, the directory must exist.  
  
 Należy podać w pełni kwalifikowaną przestrzeń nazw dla pliku resources, określając ją w nazwie pliku i oddzielając od głównej nazwy plików kropką. For example, if `outputFilename` is `MyCompany.Libraries.Strings.resources`, the namespace is MyCompany.Libraries.  
  
 Poniższe polecenie odczytuje pary nazwa/wartość z pliku Resources.txt i zapisuje w binarnym pliku resources o nazwie Resources.resources. Nazwa pliku wyjściowego nie jest jawnie określona, więc domyślnie plik wyjściowy otrzymuje taką samą nazwę jak plik wejściowy.  
  
```console  
resgen Resources.txt   
```  
  
 Poniższe polecenie odczytuje pary nazwa/wartość z pliku Resources.restext i zapisuje w binarnym pliku zasobów o nazwie StringResources.resources.  
  
```console  
resgen Resources.restext StringResources.resources  
```  
  
 Poniższe polecenie odczytuje plik wejściowy w formacie XML o nazwie Resources.resx i zapisuje plik binarny resources o nazwie Resources.resources.  
  
```console  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>   
### <a name="converting-between-resource-file-types"></a>Konwertowanie między typami plików zasobów  
 Oprócz kompilowania plików zasobów w formacie tekstowym lub XML do plików binarnych resources, program Resgen.exe może przekonwertować dowolny obsługiwany typ pliku na dowolny inny obsługiwany typ. Oznacza to, że można wykonywać następujące konwersje:  
  
- Pliki txt i restext na pliki resx.  
  
- Pliki resx na pliki txt i restext.  
  
- Pliki resources na pliki txt i restext.  
  
- Pliki resources na pliki resx.  
  
 Składnia jest taka sama, jak pokazana w poprzedniej sekcji.  
  
 In addition, you can use Resgen.exe to convert embedded resources in a .NET Framework assembly to a .resw file tor Windows 8.x Store apps.  
  
 Poniższe polecenie odczytuje binarny plik zasobów Resources.resources i zapisuje plik wyjściowy w formacie XML o nazwie Resources.resx.  
  
```console  
resgen Resources.resources Resources.resx  
```  
  
 Poniższe polecenie odczytuje plik zasobów w formacie tekstowym o nazwie StringResources.txt i zapisuje plik zasobów w formacie XML o nazwie LibraryResources.resx. Ponadto pliku resx można użyć, oprócz przechowywania zasobów w postaci ciągów, do przechowywania zasobów niebędących ciągami.  
  
```console  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Poniższe dwa polecenia odczytują plik zasobów w formacie XML o nazwie Resources.resx i zapisują pliki tekstowe o nazwach Resources.txt i Resources.restext. Należy zauważyć, że jeżeli plik resx zawiera jakiekolwiek obiekty osadzone, nie zostaną one dokładnie przekonwertowane na pliki tekstowe.  
  
```console  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>   
### <a name="compiling-or-converting-multiple-files"></a>Kompilowanie lub konwertowanie wielu plików  
 You can use the `/compile` switch to convert a list of resource files from one format to another in a single operation. Składnia jest następująca:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Poniższe polecenie kompiluje trzy pliki, StringResources.txt, TableResources.resw i ImageResources.resw, do oddzielnych plików resources o nazwach StringResources.resources, TableResources.resources i ImageResources.resources.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Eksportowanie zasobów do pliku resw  
 If you're developing a Windows 8.x Store app, you may want to use resources from an existing desktop app. Jednak te dwa rodzaje aplikacji obsługują różne formaty plików. W aplikacjach komputerowych zasoby w plikach tekstowych (txt lub restex) lub w plikach resx są kompilowane do binarnych plików resources. In Windows 8.x Store apps, .resw files are compiled into binary package resource index (PRI) files. You can use Resgen.exe to bridge this gap by extracting resources from an executable or a satellite assembly and writing them to one or more .resw files that can be used when developing a Windows 8.x Store app.  
  
> [!IMPORTANT]
> Visual Studio automatically handles all conversions necessary for incorporating the resources in a portable library into a Windows 8.x Store app. Using Resgen.exe directly to convert the resources in an assembly to .resw file format is of interest only to developers who want to develop a Windows 8.x Store app outside of Visual Studio.  
  
 Składnia służąca do generowania plików resw z zestawu jest następująca:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 gdzie parametrami są:  
  
 `filename.extension`  
 Nazwa zestawu programu .NET Framework (plik wykonywalny lub biblioteka DLL). Jeśli plik nie zawiera żadnych zasobów, program Resgen.exe nie tworzy żadnych plików.  
  
 `outputDirectory`  
 Istniejący katalog, w którym mają zostać zapisane pliki resw. If `outputDirectory` is omitted, .resw files are written to the current directory. Program Resgen.exe tworzy jeden plik resw dla każdego pliku resources w zestawie. Główna nazwa pliku resw jest taka sama jak główna nazwa pliku resources.  
  
 Poniższe polecenie tworzy plik resw w katalogu Win8Resources dla każdego pliku resources osadzonego w zestawie MyApp.exe:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Warunkowe kompilowanie zasobów  
 Starting with the .NET Framework 4.5, Resgen.exe supports conditional compilation of string resources in text (.txt and .restext) files. Dzięki temu można używać pojedynczego pliku zasobów w formacie tekstowym w wielu konfiguracjach kompilacji.  
  
 In a .txt or .restext file, you use the `#ifdef`…`#endif` construct to include a resource in the binary .resources file if a symbol is defined, and you use the `#if !`... `#endif` construct to include a resource if a symbol is not defined. At compile time, you then define symbols by using the `/define:` option followed by a comma-delimited list of symbols. The comparison is cased-sensitive; the case of symbols defined by `/define` must match the case of symbols in the text files to be compiled.  
  
 For example, the following file named UIResources.rext includes a string resource named `AppTitle` that can take one of three values, depending on whether symbols named `PRODUCTION`, `CONSULT`, or `RETAIL` are defined.  
  
```text
#ifdef PRODUCTION  
AppTitle=My Software Company Project Manager   
#endif  
#ifdef CONSULT  
AppTitle=My Consulting Company Project Manager  
#endif  
#ifdef RETAIL  
AppTitle=My Retail Store Project Manager  
#endif  
FileMenuName=File  
```  
  
 Następnie plik można skompilować do binarnego pliku resources, używając następującego polecenia:  
  
```console  
resgen /define:CONSULT UIResources.restext  
```  
  
 To polecenie utworzy plik resources zawierający dwa zasoby w postaci ciągów. The value of the `AppTitle` resource is "My Consulting Company Project Manager".  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generowanie silnie typizowanej klasy zasobów  
 Program Resgen.exe obsługuje silnie typizowane zasoby, które hermetyzują dostęp do zasobów przez tworzenie klas zawierających zestaw statycznych właściwości tylko do odczytu. This provides an alternative to calling the methods of the <xref:System.Resources.ResourceManager> class directly to retrieve resources. You can enable strongly typed resource support by using the `/str` option in Resgen.exe, which wraps the functionality of the <xref:System.Resources.Tools.StronglyTypedResourceBuilder> class. When you specify the `/str` option, the output of Resgen.exe is a class that contains strongly typed properties that match the resources that are referenced in the input parameter. Ta klasa dostarcza silnie typizowany dostęp tylko do odczytu do zasobów, które są dostępne w przetwarzanym pliku.  
  
 Składania służąca do tworzenia silnie typizowanych zasobów jest następująca:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry i przełączniki są następujące:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, dla którego należy wygenerować silnie typizowaną klasę zasobów. Plik może być plikiem tekstowym, plikiem w formacie XML lub binarnym plikiem resources; może mieć rozszerzenie txt, restext, resw lub resources.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. If `outputFilename` includes a directory path, the directory must exist. If you omit `outputFilename`, Resgen.exe creates a .resources file with the root file name of `inputFilename` in the same directory as `inputFilename`.  
  
 `outputFilename` can be a text-based, XML-based, or binary .resources file. If the file extension of `outputFilename` is different from the file extension of `inputFilename`, Resgen.exe performs the file conversion.  
  
 If `inputFilename` is a .resources file, Resgen.exe copies the .resources file if `outputFilename` is also a .resources file. If `outputFilename` is omitted, Resgen.exe overwrites `inputFilename` with an identical .resources file.  
  
 *language*  
 Język, w którym należy wygenerować kod źródłowy dla silnie typizowanej klasy zasobów. Possible values are `cs`, `C#`, and `csharp` for C# code, `vb` and `visualbasic` for Visual Basic code, `vbs` and `vbscript` for VBScript code, and `c++`, `mc`, and `cpp` for C++ code.  
  
 *namespace*  
 Przestrzeń nazw zawierająca silnie typizowaną klasę zasobów. Plik resources i klasa zasobów powinny mieć taką samą przestrzeń nazw. For information about specifying the namespace in the `outputFilename`, see [Compiling Resources into a Binary File](resgen-exe-resource-file-generator.md#Compiling). If *namespace* is omitted, the resource class is not contained in a namespace.  
  
 *classname*  
 Nazwa silnie typizowanej klasy zasobów. Powinna odpowiadać głównej nazwie pliku resources. Na przykład jeśli program Resgen.exe generuje plik resources o nazwie MyCompany.Libraries.Strings.resources, nazwa silnie typizowanej klasy zasobów to Strings. If *classname* is omitted, the generated class is derived from the root name of `outputFilename`. If `outputFilename` is omitted, the generated class is derived from the root name of `inputFilename`.  
  
 *classname* cannot contain invalid characters such as embedded spaces. If *classname* contains embedded spaces, or if *classname* is generated by default from *inputFilename*, and *inputFilename* contains embedded spaces, Resgen.exe replaces all invalid characters with an underscore (\_).  
  
 *filename*  
 Nazwa pliku klasy.  
  
 `/publicclass`  
 Makes the strongly typed resource class public rather than `internal` (in C#) or `Friend` (in Visual Basic). Dzięki temu zasoby będą dostępne spoza zestawu, w którym są osadzone.  
  
> [!IMPORTANT]
> Podczas tworzenia silnie typizowanej klasy zasobów nazwa pliku resources musi odpowiadać przestrzeni nazw i nazwie klasy generowanego kodu. Jednak program Resgen.exe umożliwia określenie opcji, które tworzą plik resources mający niezgodną nazwę. Aby obejść ten problem, należy zmienić nazwę pliku wyjściowego po jego wygenerowaniu.  
  
 Silnie typizowana klasa zasobów ma następujące składowe:  
  
- A parameterless constructor, which can be used to instantiate the strongly typed resource class.  
  
- A `static` (C#) or `Shared` (Visual Basic) and read-only `ResourceManager` property, which returns the <xref:System.Resources.ResourceManager> instance that manages the strongly typed resource.  
  
- A static `Culture` property, which allows you to set the culture used for resource retrieval. By default, its value is `null`, which means that the current UI culture is used.  
  
- One `static` (C#) or `Shared` (Visual Basic) and read-only property for each resource in the .resources file. Nazwa właściwości to nazwa zasobu.  
  
 For example, the following command compiles a resource file named StringResources.txt into StringResources.resources and generates a class named `StringResources` in a Visual Basic source code file named StringResources.vb that can be used to access the Resource Manager.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Zasoby w aplikacjach klasycznych](../resources/index.md)
- [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (konsolidator zestawów)](al-exe-assembly-linker.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
