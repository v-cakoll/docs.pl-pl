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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db85781b48fd75c3d2ef70834fd8451647f6917
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044221"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Generator pliku zasobów)
Generator plików zasobów (Resgen.exe) konwertuje pliki tekstowe (txt lub restext) i pliki zasobów w formacie XML (resx) na pliki binarne (resources) środowiska uruchomieniowego języka wspólnego, które można osadzić w binarnym pliku wykonywalnym środowiska uruchomieniowego lub zestawie satelickim. (Zobacz [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md)).  
  
 Program Resgen.exe to uniwersalne narzędzie do konwersji zasobów, które wykonuje następujące zadania:  
  
- Konwertuje pliki txt lub restext na pliki resx lub resources. (Format plików restext jest identyczny z formatem plików txt. Jednak rozszerzenie restext pomaga łatwiej zidentyfikować pliki tekstowe, które zawierają definicje zasobów).  
  
- Konwertuje pliki resources na pliki tekstowe lub resx.  
  
- Konwertuje pliki resx na pliki tekstowe lub resources.  
  
- Wyodrębnia zasoby ciągu z zestawu do pliku RESW, który jest odpowiedni do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
- Tworzy klasę o jednoznacznie określonym typie, która zapewnia dostęp do poszczególnych nazwanych zasobów <xref:System.Resources.ResourceManager> i do wystąpienia.  
  
 Jeśli działanie programu Resgen.exe kończy się niepowodzeniem z dowolnej przyczyny, zwracaną wartością jest -1.  
  
 Aby uzyskać pomoc dotyczącą programu Resgen.exe, należy użyć następującego polecenia, bez określania żadnych opcji, w celu wyświetlenia składni polecenia i opcji programu Resgen.exe:  
  
```console  
resgen  
```  
  
 Można również użyć `/?` przełącznika:  
  
```console  
resgen /?  
```  
  
 Jeśli używasz Resgen, exe do generowania plików binarnych. resources, możesz użyć kompilatora języka do osadzenia plików binarnych w zestawach wykonywalnych lub użyć [konsolidatora zestawu (Al. exe)](al-exe-assembly-linker.md) , aby skompilować je do zestawów satelickich.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
resgen  [/define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```console  
resgen filename.extension [outputDirectory]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr lub opcja|Opis|  
|-------------------------|-----------------|  
|`/define:`*symbol1* [, *symbol2*,...]|Począwszy od .NET Framework 4,5, obsługuje kompilacji warunkowej w plikach zasobów tekstowych (. txt lub. restext). Jeśli *symbol* odnosi się do symbolu zawartego w wejściowym pliku tekstowym w `#ifdef` konstrukcji, skojarzony zasób ciągu jest zawarty w pliku Resources. Jeśli wejściowy plik tekstowy zawiera `#if !` instrukcję z symbolem, który nie jest zdefiniowany `/define` przez przełącznik, skojarzony zasób ciągu jest zawarty w pliku Resources.<br /><br /> `/define`jest ignorowany, jeśli jest używany z plikami nietekstowymi. W symbolach jest uwzględniania wielkość liter.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [warunkowe Kompilowanie zasobów](#Conditional) w dalszej części tego tematu.|  
|`useSourcePath`|Określa, że bieżący katalog pliku wejściowego ma być używany na potrzeby rozpoznawania względnych ścieżek plików.|  
|`/compile`|Umożliwia określenie wielu plików tekstowych lub resx w celu konwersji na wiele plików resources w pojedynczej zbiorczej operacji. Jeśli ta opcja nie jest określona, można określić tylko jeden argument pliku wejściowego. Pliki wyjściowe mają nazwę *filename*. resources.<br /><br /> Tej opcji nie można używać z `/str:` opcją.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [Kompilowanie lub konwertowanie wielu plików](#Multiple) w dalszej części tego tematu.|  
|`/r:``assembly`|Odwołuje się do metadanych z określonego zestawu. Jest używana podczas konwersji plików resx i zezwala programowi Resgen.exe na serializację lub deserializację zasobów obiektu. Jest on podobny do `/reference:` opcji lub `/r:` dla kompilatorów C# i Visual Basic.|  
|`filename.extension`|Określa nazwę pliku wejściowego do konwersji. Jeśli używasz pierwszej dłuższa składni wiersza polecenia przedstawionej przed tą tabelą, `extension` musi to być jedna z następujących:<br /><br /> .txt lub .restext<br /> Plik tekstowy do konwersji na plik resources lub resx. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów. Aby uzyskać informacje o formacie pliku, zobacz sekcję "zasoby w plikach tekstowych" w temacie [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Plik zasobów w języku XML do konwersji na plik .resources lub plik tekstowy (txt lub restext).<br /><br /> .resources<br /> Plik binarny zasobów do konwersji na plik resx lub plik tekstowy (txt lub restext).<br /><br /> Jeśli używasz drugiej, krótszej składni wiersza polecenia przedstawionej przed tą tabelą, `extension` należy wykonać następujące czynności:<br /><br /> .exe lub .dll<br /> Zestaw .NET Framework (plik wykonywalny lub biblioteka), którego zasoby ciągu mają zostać wyodrębnione do pliku. resw do użycia podczas [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] tworzenia aplikacji.|  
|`outputFilename.extension`|Określa nazwę i typ tworzonego pliku zasobów.<br /><br /> Ten argument jest opcjonalny podczas konwersji z pliku txt, restext lub resx na plik resources. Jeśli nie określisz `outputFilename`, Resgen. exe dołącza rozszerzenie. resources do danych wejściowych `filename` i zapisuje plik w katalogu, który zawiera `filename,extension`.<br /><br /> `outputFilename.extension` Argument jest obowiązkowy podczas konwersji z pliku Resources. Określa nazwę pliku z rozszerzeniem resx podczas konwersji pliku resources na plik zasobów w formacie XML. Określa nazwę pliku z rozszerzeniem txt lub restext podczas konwersji na plik resources lub plik tekstowy. Plik resources należy konwertować na plik txt tylko wtedy, gdy plik resources zawiera wyłącznie wartości w postaci ciągów.|  
|`outputDirectory`|W [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] przypadku aplikacji określa katalog, w którym `filename.extension` zostanie zapisany plik. resw zawierający zasoby ciągu. `outputDirectory`musi już istnieć.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Tworzy plik klasy zasobów o jednoznacznie określonym typie w języku programowania określonym w `language` opcji. `language`może składać się z jednego z następujących literałów:<br /><br /> -Dla C#: `c#`, `cs`lub. `csharp`<br />-Dla Visual Basic: `vb` lub `visualbasic`.<br />— Dla języka VBScript `vbs` : `vbscript`lub.<br />-Dla C++: `c++`, `mc`lub. `cpp`<br />— W przypadku języka `js`JavaScript `jscript`:, `javascript`lub.<br /><br /> Opcja określa domyślną przestrzeń nazw projektu `classname` , opcja określa nazwę `filename` wygenerowanej klasy, a opcja określa nazwę pliku klasy. `namespace`<br /><br /> Opcja `/str:` zezwala na tylko jeden plik wejściowy, dlatego nie można jej używać `/compile` z opcją.<br /><br /> Jeśli `namespace` jest określony, `classname` ale nie jest, nazwa klasy pochodzi od nazwy pliku wyjściowego (na przykład podkreślenia są zastępowane dla kropek). Zasoby silnie typizowane mogą nie działać poprawnie jako wynik. Aby tego uniknąć, należy określić zarówno nazwę klasy, jak i nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [Generowanie klasy zasobów o jednoznacznie określonym typie](#Strong) w dalszej części tego tematu.|  
|`/publicClass`|Tworzy silnie typizowaną klasę zasobu jako klasę publiczną. Domyślnie Klasa zasobów jest `internal` w C# i `Friend` w Visual Basic.<br /><br /> Ta opcja jest ignorowana, `/str:` Jeśli opcja nie jest używana.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Program Resgen.exe i typy plików zasobów  
 Aby program Resgen.exe mógł pomyślnie konwertować zasoby, pliki tekstowe i resx muszą mieć poprawny format.  
  
### <a name="text-txt-and-restext-files"></a>Pliki tekstowe (txt i restext)  
 Pliki tekstowe (txt lub restext) mogą zawierać tylko zasoby w postaci ciągów. Zasoby w postaci ciągów są przydatne podczas pisania aplikacji, która musi być przetłumaczona na kilka języków. Na przykład można łatwo poddać regionalizacji napisy w menu przy użyciu odpowiedniego zasobu w postaci ciągu. Program Resgen.exe odczytuje pliki tekstowe, które zawierają pary nazwa/wartość, gdzie nazwa jest ciągiem opisującym zasób, a wartość to właśnie ciąg zasobu.  
  
> [!NOTE]
> Aby uzyskać informacje na temat formatu plików txt i. restext, zobacz sekcję "zasoby w plikach tekstowych" [tworzenia plików zasobów](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Plik tekstowy, który zawiera zasoby, musi być zapisany z użyciem kodowania UTF-8 lub Unicode (UTF-16), chyba że zawiera tylko znaki z zakresu Łaciński podstawowy (do U+007F). Program Resgen.exe usuwa rozszerzone znaki ANSI podczas przetwarzania pliku tekstowego, który został zapisany przy użyciu kodowania ANSI.  
  
 Program Resgen.exe sprawdza, czy plik tekstowy zawiera zduplikowane nazwy zasobów. Jeśli plik tekstowy zawiera zduplikowane nazwy zasobów, program Resgen.exe wyświetli ostrzeżenie i zignoruje drugą wartość.  
  
### <a name="resx-files"></a>Pliki resx  
 Format plików zasobów resx składa się z wpisów XML. Można określić zasoby w postaci ciągów w tych wpisach XML, tak jak w plikach tekstowych. Główną zaletą plików resx w porównaniu z plikami tekstowymi jest to, że można określić lub osadzić w nich obiekty. Podczas przeglądania pliku resx można zobaczyć binarną formę osadzonego obiektu (na przykład obrazka), gdy te informacje binarne są częścią manifestu zasobu. Tak jak w przypadku plików tekstowych, plik resx można otworzyć za pomocą edytora tekstów (takiego jak Notatnik lub program Microsoft Word), a następnie można pisać i analizować jego zawartość, a także wykonywać na niej różne operacje. Należy zauważyć, że wymaga to dobrej znajomości tagów XML i struktury pliku resx. Aby uzyskać więcej informacji o formacie pliku resx, zobacz sekcję "zasoby w plikach resx" tematu [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Aby utworzyć plik resources zawierający osadzone obiekty niebędące ciągami, musisz użyć Resgen. exe do przekonwertowania pliku resx zawierającego obiekty lub dodać zasoby obiektów do pliku bezpośrednio z kodu, wywołując metody dostarczone przez <xref:System.Resources.ResourceWriter> określonej.  
  
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
 Programu Resgen. exe można używać na różne sposoby: do kompilowania pliku zasobów tekstowego lub XML do pliku binarnego, konwersji między formatami plików zasobów i generowania klasy, która zawija <xref:System.Resources.ResourceManager> funkcjonalność i zapewnia dostęp do zasobów. Ta sekcja zawiera szczegółowe informacje dotyczące każdego zadania:  
  
- [Kompilowanie zasobów do pliku binarnego](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Konwertowanie między typami plików zasobów](resgen-exe-resource-file-generator.md#Convert)  
  
- [Kompilowanie lub konwertowanie wielu plików](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Eksportowanie zasobów do pliku. resw](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Warunkowe Kompilowanie zasobów](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generowanie klasy zasobów o jednoznacznie określonym typie](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilowanie zasobów do pliku binarnego  
 Najbardziej powszechnym zastosowaniem programu Resgen.exe jest kompilacja pliku zasobów w formacie tekstowym (pliku txt lub restext) lub w formacie XML (pliku resx) do pliku binarnego resources. Plik wyjściowy może zostać osadzony w zestawie głównym przez kompilator języka lub w zestawie satelickim przez [konsolidator zestawu (Al. exe)](al-exe-assembly-linker.md).  
  
 Składnia służąca do kompilacji pliku zasobów jest następująca:  
  
```console  
resgen inputFilename [outputFilename]   
```  
  
 gdzie parametrami są:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, który należy skompilować. Program Resgen.exe kompiluje tylko pliki z rozszerzeniem txt, restext lub resx.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. Jeśli pominięto `outputFilename`, Resgen. exe tworzy plik resources o `inputFilename` nazwie pliku głównego w tym samym katalogu, co `inputFilename`. Jeśli `outputFilename` zawiera ścieżkę katalogu, katalog musi istnieć.  
  
 Należy podać w pełni kwalifikowaną przestrzeń nazw dla pliku resources, określając ją w nazwie pliku i oddzielając od głównej nazwy plików kropką. Na przykład, jeśli `outputFilename` jest `MyCompany.Libraries.Strings.resources`, przestrzeń nazw to webcompany. librarys.  
  
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
  
 Ponadto można użyć programu Resgen. exe do przekonwertowania osadzonych zasobów w zestawie .NET Framework do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji resw.  
  
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
 Możesz użyć przełącznika, `/compile` Aby skonwertować listę plików zasobów z jednego formatu do innego w ramach jednej operacji. Składnia jest następująca:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Poniższe polecenie kompiluje trzy pliki, StringResources.txt, TableResources.resw i ImageResources.resw, do oddzielnych plików resources o nazwach StringResources.resources, TableResources.resources i ImageResources.resources.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Eksportowanie zasobów do pliku resw  
 Jeśli tworzysz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację, możesz chcieć używać zasobów z istniejącej aplikacji klasycznej. Jednak te dwa rodzaje aplikacji obsługują różne formaty plików. W aplikacjach komputerowych zasoby w plikach tekstowych (txt lub restex) lub w plikach resx są kompilowane do binarnych plików resources. W [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacjach pliki. resw są kompilowane do plików binarnych (PRI) pakietu. Można użyć Resgen. exe do mostkowania tej przerwy przez wyodrębnienie zasobów z pliku wykonywalnego lub zestawu satelickiego i zapisanie ich do jednego lub więcej plików. resw, które mogą być używane [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] podczas tworzenia aplikacji.  
  
> [!IMPORTANT]
> Program Visual Studio automatycznie obsługuje wszystkie konwersje niezbędne do włączenia zasobów w bibliotece przenośnej do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Używanie programu Resgen. exe bezpośrednio do konwertowania zasobów w zestawie na format pliku RESW jest istotne tylko dla deweloperów, którzy chcą opracowywać [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację poza programem Visual Studio.  
  
 Składnia służąca do generowania plików resw z zestawu jest następująca:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 gdzie parametrami są:  
  
 `filename.extension`  
 Nazwa zestawu programu .NET Framework (plik wykonywalny lub biblioteka DLL). Jeśli plik nie zawiera żadnych zasobów, program Resgen.exe nie tworzy żadnych plików.  
  
 `outputDirectory`  
 Istniejący katalog, w którym mają zostać zapisane pliki resw. W `outputDirectory` przypadku pominięcia pliki. resw są zapisywane w bieżącym katalogu. Program Resgen.exe tworzy jeden plik resw dla każdego pliku resources w zestawie. Główna nazwa pliku resw jest taka sama jak główna nazwa pliku resources.  
  
 Poniższe polecenie tworzy plik resw w katalogu Win8Resources dla każdego pliku resources osadzonego w zestawie MyApp.exe:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Warunkowe kompilowanie zasobów  
 Począwszy od .NET Framework 4,5, Resgen. exe obsługuje kompilację warunkową zasobów ciągów w plikach tekstowych (txt i. restext). Dzięki temu można używać pojedynczego pliku zasobów w formacie tekstowym w wielu konfiguracjach kompilacji.  
  
 W pliku txt lub. restext używasz `#ifdef`...`#endif` konstrukcja do uwzględnienia zasobu w pliku Binary. resources, jeśli jest zdefiniowany symbol i `#if !`używasz... `#endif` konstrukcja umożliwiająca uwzględnienie zasobu, jeśli symbol nie jest zdefiniowany. W czasie kompilacji można definiować symbole przy użyciu opcji, `/define:` a po niej rozdzielone przecinkami listę symboli. Porównanie uwzględnia wielkość liter; przypadek symboli zdefiniowany przez `/define` musi odpowiadać wielkości liter symboli w plikach tekstowych do skompilowania.  
  
 Na przykład następujący plik o nazwie UIResources. rext zawiera zasób `AppTitle` ciągu o nazwie, który może przyjmować jedną z trzech wartości, w zależności od tego, czy są zdefiniowane symbole o nazwach `PRODUCTION`, `CONSULT`lub `RETAIL` .  
  
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
  
 To polecenie utworzy plik resources zawierający dwa zasoby w postaci ciągów. Wartość `AppTitle` zasobu to "My konsultingowego menedżera projektu firmy".  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generowanie silnie typizowanej klasy zasobów  
 Program Resgen.exe obsługuje silnie typizowane zasoby, które hermetyzują dostęp do zasobów przez tworzenie klas zawierających zestaw statycznych właściwości tylko do odczytu. Zapewnia to alternatywę do wywoływania metod <xref:System.Resources.ResourceManager> klasy bezpośrednio w celu pobierania zasobów. Obsługę zasobów o jednoznacznie określonym typie można włączyć przy użyciu `/str` opcji w programie Resgen. exe, która otacza funkcjonalność <xref:System.Resources.Tools.StronglyTypedResourceBuilder> klasy. Po określeniu `/str` opcji dane wyjściowe programu Resgen. exe to Klasa, która zawiera właściwości o jednoznacznie określonym typie, które pasują do zasobów, do których odwołuje się parametr wejściowy. Ta klasa dostarcza silnie typizowany dostęp tylko do odczytu do zasobów, które są dostępne w przetwarzanym pliku.  
  
 Składania służąca do tworzenia silnie typizowanych zasobów jest następująca:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry i przełączniki są następujące:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, dla którego należy wygenerować silnie typizowaną klasę zasobów. Plik może być plikiem tekstowym, plikiem w formacie XML lub binarnym plikiem resources; może mieć rozszerzenie txt, restext, resw lub resources.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. Jeśli `outputFilename` zawiera ścieżkę katalogu, katalog musi istnieć. Jeśli pominięto `outputFilename`, Resgen. exe tworzy plik resources o `inputFilename` nazwie pliku głównego w tym samym katalogu, co `inputFilename`.  
  
 `outputFilename`może to być plik tekstowy, oparty na języku XML lub binarny. resources. Jeśli rozszerzenie `outputFilename` pliku jest inne niż `inputFilename`rozszerzenie pliku, program Resgen. exe wykonuje konwersję plików.  
  
 Jeśli `inputFilename` jest to plik resources, Resgen. exe kopiuje plik resources `outputFilename` , jeśli również jest to plik resources. W `outputFilename` przypadku pominięcia programu Resgen. exe `inputFilename` zastępuje ten sam plik resources.  
  
 *językowe*  
 Język, w którym należy wygenerować kod źródłowy dla silnie typizowanej klasy zasobów. Możliwe wartości to `cs`, `C#`, i `csharp` dla C# kodu, `vb` i `visualbasic` dla kodu Visual Basic, `vbs` a `vbscript` w przypadku kodu VBScript i `c++` `mc`,, i `cpp` dla C++ kodu.  
  
 *namespace*  
 Przestrzeń nazw zawierająca silnie typizowaną klasę zasobów. Plik resources i klasa zasobów powinny mieć taką samą przestrzeń nazw. Aby uzyskać informacje o określaniu przestrzeni nazw `outputFilename`w programie, zobacz [Kompilowanie zasobów do pliku binarnego](resgen-exe-resource-file-generator.md#Compiling). W przypadku pominięcia *przestrzeni nazw* Klasa zasobów nie jest zawarta w przestrzeni nazw.  
  
 *nazwą*  
 Nazwa silnie typizowanej klasy zasobów. Powinna odpowiadać głównej nazwie pliku resources. Na przykład jeśli program Resgen.exe generuje plik resources o nazwie MyCompany.Libraries.Strings.resources, nazwa silnie typizowanej klasy zasobów to Strings. Jeśli *ClassName* zostanie pominięty, wygenerowana Klasa jest pochodną nazwy `outputFilename`głównej. W `outputFilename` przypadku pominięcia wygenerowana Klasa jest pochodną `inputFilename`nazwy głównej.  
  
 *ClassName* nie może zawierać nieprawidłowych znaków, takich jak spacje osadzone. Jeśli *ClassName* zawiera osadzone spacje lub jeśli *ClassName* jest generowana domyślnie z *inputFilename*, a *inputFilename* zawiera osadzone spacje, Resgen. exe zastępuje wszystkie nieprawidłowe znaki znakiem podkreślenia (\_).  
  
 *Nazwa pliku*  
 Nazwa pliku klasy.  
  
 `/publicclass`  
 Sprawia, że Klasa zasobów o jednoznacznie określonym typie `internal` powinna być C#publiczna `Friend` , a nie (w) lub (w Visual Basic). Dzięki temu zasoby będą dostępne spoza zestawu, w którym są osadzone.  
  
> [!IMPORTANT]
> Podczas tworzenia silnie typizowanej klasy zasobów nazwa pliku resources musi odpowiadać przestrzeni nazw i nazwie klasy generowanego kodu. Jednak program Resgen.exe umożliwia określenie opcji, które tworzą plik resources mający niezgodną nazwę. Aby obejść ten problem, należy zmienić nazwę pliku wyjściowego po jego wygenerowaniu.  
  
 Silnie typizowana klasa zasobów ma następujące składowe:  
  
- Konstruktor bez parametrów, którego można użyć do utworzenia wystąpienia silnie typizowanej klasy zasobów.  
  
- A `static` (C#) lub `Shared` (Visual Basic) i właściwość tylko `ResourceManager` do odczytu, która zwraca <xref:System.Resources.ResourceManager> wystąpienie zarządzające silnie określonym zasobem.  
  
- Właściwość statyczna `Culture` , która pozwala ustawić kulturę używaną do pobierania zasobów. Domyślnie jego wartość to `null`, co oznacza, że jest używana bieżąca kultura interfejsu użytkownika.  
  
- Jeden `static` (C#) lub `Shared` (Visual Basic) i właściwość tylko do odczytu dla każdego zasobu w pliku Resources. Nazwa właściwości to nazwa zasobu.  
  
 Na przykład następujące polecenie kompiluje plik zasobów o nazwie StringResources. txt do StringResources. resources i generuje klasę o nazwie `StringResources` w Visual Basic źródłowym pliku o nazwie StringResources. vb, której można użyć w celu uzyskania dostępu do zasobu Menedżera.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Zasoby w aplikacjach klasycznych](../resources/index.md)
- [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (konsolidator zestawów)](al-exe-assembly-linker.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
