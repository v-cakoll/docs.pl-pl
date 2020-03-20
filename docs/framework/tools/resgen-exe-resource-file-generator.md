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
ms.openlocfilehash: cf79e7c76fd54c6cb6b235251a57aba33c28552b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180329"
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Generator pliku zasobów)
Generator plików zasobów (Resgen.exe) konwertuje pliki tekstowe (txt lub restext) i pliki zasobów w formacie XML (resx) na pliki binarne (resources) środowiska uruchomieniowego języka wspólnego, które można osadzić w binarnym pliku wykonywalnym środowiska uruchomieniowego lub zestawie satelickim. (Zobacz [Tworzenie plików zasobów).](../resources/creating-resource-files-for-desktop-apps.md)  
  
 Program Resgen.exe to uniwersalne narzędzie do konwersji zasobów, które wykonuje następujące zadania:  
  
- Konwertuje pliki txt lub restext na pliki resx lub resources. (Format plików restext jest identyczny z formatem plików txt. Jednak rozszerzenie restext pomaga łatwiej zidentyfikować pliki tekstowe, które zawierają definicje zasobów).  
  
- Konwertuje pliki resources na pliki tekstowe lub resx.  
  
- Konwertuje pliki resx na pliki tekstowe lub resources.  
  
- Wyodrębnia zasoby ciągu z zestawu do pliku .resw, który jest odpowiedni do użycia w aplikacji ze Sklepu Windows 8.x.  
  
- Tworzy silnie typizowana klasa, która zapewnia dostęp <xref:System.Resources.ResourceManager> do poszczególnych nazwanych zasobów i do wystąpienia.  
  
 Jeśli działanie programu Resgen.exe kończy się niepowodzeniem z dowolnej przyczyny, zwracaną wartością jest -1.  
  
 Aby uzyskać pomoc dotyczącą programu Resgen.exe, można użyć następującego polecenia, bez określonych opcji, aby wyświetlić składnię polecenia i opcje programu Resgen.exe:  
  
```console  
resgen  
```  
  
 Można również użyć `/?` przełącznika:  
  
```console  
resgen /?  
```  
  
 Jeśli używasz Programu Resgen.exe do generowania plików binarnych .resources, można użyć kompilatora języka, aby osadzić pliki binarne w zestawach wykonywalnych lub użyć [zestawu Łączącego (Al.exe)](al-exe-assembly-linker.md) do kompilowania ich w zestawy satelitarne.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
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
|`/define:`*symbol1*[, *symbol2*,...]|Począwszy od programu .NET Framework 4.5, obsługuje kompilację warunkową w plikach zasobów tekstowych (txt lub .restext). Jeśli *symbol* odpowiada symbolowi zawartemu w wejściowym `#ifdef` pliku tekstowym w konstrukcji, skojarzony zasób ciągu jest zawarty w pliku .resources. Jeśli wejściowy plik `#if !` tekstowy zawiera instrukcję z `/define` symbolem, który nie jest zdefiniowany przez przełącznik, skojarzony zasób ciągu jest zawarty w pliku zasobów.<br /><br /> `/define`jest ignorowana, jeśli jest używana z plikami nietekstowymi. W symbolach jest uwzględniania wielkość liter.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [warunkowe kompilowanie zasobów](#Conditional) w dalszej części tego tematu.|  
|`useSourcePath`|Określa, że bieżący katalog pliku wejściowego ma być używany na potrzeby rozpoznawania względnych ścieżek plików.|  
|`/compile`|Umożliwia określenie wielu plików tekstowych lub resx w celu konwersji na wiele plików resources w pojedynczej zbiorczej operacji. Jeśli ta opcja nie jest określona, można określić tylko jeden argument pliku wejściowego. Pliki wyjściowe są nazywane *nazwami plików*.resources.<br /><br /> Tej opcji nie można `/str:` używać z opcją.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [Kompilowanie lub konwertowanie wielu plików](#Multiple) w dalszej części tego tematu.|  
|`/r:` `assembly`|Odwołuje się do metadanych z określonego zestawu. Jest używana podczas konwersji plików resx i zezwala programowi Resgen.exe na serializację lub deserializację zasobów obiektu. Jest podobny do `/reference:` `/r:` lub opcje dla kompilatorów Języka C# i Visual Basic.|  
|`filename.extension`|Określa nazwę pliku wejściowego do konwersji. Jeśli używasz pierwszej, dłuższej składni wiersza polecenia przedstawionej `extension` przed tą tabelą, musi być jedną z następujących czynności:<br /><br /> .txt lub .restext<br /> Plik tekstowy do konwersji na plik resources lub resx. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów. Aby uzyskać informacje o formacie pliku, zobacz sekcję "Zasoby w plikach tekstowych" w sekcji [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Plik zasobów w języku XML do konwersji na plik .resources lub plik tekstowy (txt lub restext).<br /><br /> .resources<br /> Plik binarny zasobów do konwersji na plik resx lub plik tekstowy (txt lub restext).<br /><br /> Jeśli używasz drugiej, krótszej składni wiersza polecenia przedstawionej przed tą tabelą, `extension` musi być następująca:<br /><br /> .exe lub .dll<br /> Zestaw .NET Framework (plik wykonywalny lub biblioteka), którego zasoby ciągu mają być wyodrębnione do pliku resw do użycia w tworzeniu aplikacji ze Sklepu Windows 8.x.|  
|`outputFilename.extension`|Określa nazwę i typ tworzonego pliku zasobów.<br /><br /> Ten argument jest opcjonalny podczas konwersji z pliku txt, restext lub resx na plik resources. Jeśli nie określisz `outputFilename`, Program Resgen.exe dołącza rozszerzenie `filename` .resources do danych wejściowych i `filename,extension`zapisuje plik w katalogu zawierającym .<br /><br /> Argument `outputFilename.extension` jest obowiązkowy podczas konwersji z pliku .resources. Określa nazwę pliku z rozszerzeniem resx podczas konwersji pliku resources na plik zasobów w formacie XML. Określa nazwę pliku z rozszerzeniem txt lub restext podczas konwersji na plik resources lub plik tekstowy. Plik resources należy konwertować na plik txt tylko wtedy, gdy plik resources zawiera wyłącznie wartości w postaci ciągów.|  
|`outputDirectory`|W przypadku aplikacji ze Sklepu Windows 8.x określa katalog, w którym `filename.extension` zostanie zapisany plik resw zawierający zasoby ciągów. `outputDirectory`muszą już istnieć.|  
|`/str:` `language[,namespace[,classname[,filename]]]`|Tworzy silnie typiwany plik klasy zasobów w `language` języku programowania określonym w opcji. `language`może składać się z jednego z następujących literałów:<br /><br /> - Dla C#: `c#`, `cs`, lub `csharp`.<br />- Dla Visual `vb` `visualbasic`Basic: lub .<br />- Dla VBScript: `vbs` lub `vbscript`.<br />- Dla C++: `c++`, `mc`, lub `cpp`.<br />- W przypadku `js` `jscript`Języka `javascript`JavaScript: , , lub .<br /><br /> Opcja `namespace` określa domyślny obszar nazw projektu, `classname` opcja określa nazwę wygenerowanej klasy, `filename` a opcja określa nazwę pliku klasy.<br /><br /> Opcja `/str:` ta zezwala tylko na jeden plik wejściowy, więc nie można go używać z `/compile` opcją.<br /><br /> Jeśli `namespace` jest `classname` określony, ale nie jest, nazwa klasy pochodzi od nazwy pliku wyjściowego (na przykład podkreślenia są zastępowane okresami). Zasoby silnie typizowane mogą nie działać poprawnie jako wynik. Aby tego uniknąć, należy określić zarówno nazwę klasy, jak i nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [Generowanie klasy zasobów silnie typizowane](#Strong) w dalszej części tego tematu.|  
|`/publicClass`|Tworzy silnie typizowaną klasę zasobu jako klasę publiczną. Domyślnie klasa zasobu `internal` jest w `Friend` języku C# i visual basic.<br /><br /> Ta opcja jest ignorowana, `/str:` jeśli opcja nie jest używana.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Program Resgen.exe i typy plików zasobów  
 Aby program Resgen.exe mógł pomyślnie konwertować zasoby, pliki tekstowe i resx muszą mieć poprawny format.  
  
### <a name="text-txt-and-restext-files"></a>Pliki tekstowe (txt i restext)  
 Pliki tekstowe (txt lub restext) mogą zawierać tylko zasoby w postaci ciągów. Zasoby w postaci ciągów są przydatne podczas pisania aplikacji, która musi być przetłumaczona na kilka języków. Na przykład można łatwo poddać regionalizacji napisy w menu przy użyciu odpowiedniego zasobu w postaci ciągu. Program Resgen.exe odczytuje pliki tekstowe, które zawierają pary nazwa/wartość, gdzie nazwa jest ciągiem opisującym zasób, a wartość to właśnie ciąg zasobu.  
  
> [!NOTE]
> Aby uzyskać informacje o formacie plików txt i .restext, zobacz sekcję "Zasoby w plikach tekstowych" w sekcji [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Plik tekstowy, który zawiera zasoby, musi być zapisany z użyciem kodowania UTF-8 lub Unicode (UTF-16), chyba że zawiera tylko znaki z zakresu Łaciński podstawowy (do U+007F). Program Resgen.exe usuwa rozszerzone znaki ANSI podczas przetwarzania pliku tekstowego, który został zapisany przy użyciu kodowania ANSI.  
  
 Program Resgen.exe sprawdza, czy plik tekstowy zawiera zduplikowane nazwy zasobów. Jeśli plik tekstowy zawiera zduplikowane nazwy zasobów, program Resgen.exe wyświetli ostrzeżenie i zignoruje drugą wartość.  
  
### <a name="resx-files"></a>Pliki resx  
 Format plików zasobów resx składa się z wpisów XML. Można określić zasoby w postaci ciągów w tych wpisach XML, tak jak w plikach tekstowych. Główną zaletą plików resx w porównaniu z plikami tekstowymi jest to, że można określić lub osadzić w nich obiekty. Podczas przeglądania pliku resx można zobaczyć binarną formę osadzonego obiektu (na przykład obrazka), gdy te informacje binarne są częścią manifestu zasobu. Tak jak w przypadku plików tekstowych, plik resx można otworzyć za pomocą edytora tekstów (takiego jak Notatnik lub program Microsoft Word), a następnie można pisać i analizować jego zawartość, a także wykonywać na niej różne operacje. Należy zauważyć, że wymaga to dobrej znajomości tagów XML i struktury pliku resx. Aby uzyskać więcej informacji na temat formatu pliku resx, zobacz sekcję "Zasoby w plikach resx" w temacie [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md).  
  
 Aby utworzyć plik .resources zawierający osadzone obiekty nieciągające, należy użyć programu Resgen.exe do przekonwertowania pliku .resx zawierającego obiekty lub <xref:System.Resources.ResourceWriter> dodać zasoby obiektu bezpośrednio do pliku z kodu, wywołując metody dostarczone przez klasę.  
  
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
 Program Resgen.exe można używać na różne sposoby: do kompilowania pliku zasobów opartego na tekście lub XML na plik <xref:System.Resources.ResourceManager> binarny, do konwersji między formatami plików zasobów oraz do generowania klasy, która zawija funkcjonalność i zapewnia dostęp do zasobów. Ta sekcja zawiera szczegółowe informacje dotyczące każdego zadania:  
  
- [Kompilowanie zasobów do pliku binarnego](resgen-exe-resource-file-generator.md#Compiling)  
  
- [Konwertowanie między typami plików zasobów](resgen-exe-resource-file-generator.md#Convert)  
  
- [Kompilowanie lub konwertowanie wielu plików](resgen-exe-resource-file-generator.md#Multiple)  
  
- [Eksportowanie zasobów do pliku resw](resgen-exe-resource-file-generator.md#Exporting)  
  
- [Warunkowe kompilowanie zasobów](resgen-exe-resource-file-generator.md#Conditional)  
  
- [Generowanie silnie typizowanej klasy zasobów](resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>
### <a name="compiling-resources-into-a-binary-file"></a>Kompilowanie zasobów do pliku binarnego  
 Najbardziej powszechnym zastosowaniem programu Resgen.exe jest kompilacja pliku zasobów w formacie tekstowym (pliku txt lub restext) lub w formacie XML (pliku resx) do pliku binarnego resources. Plik wyjściowy może być następnie osadzony w głównym zestawie przez kompilator języka lub w zestawie satelicie przez [zestaw zestawu (AL.exe)](al-exe-assembly-linker.md).  
  
 Składnia służąca do kompilacji pliku zasobów jest następująca:  
  
```console  
resgen inputFilename [outputFilename]
```  
  
 gdzie parametrami są:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, który należy skompilować. Program Resgen.exe kompiluje tylko pliki z rozszerzeniem txt, restext lub resx.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. Jeśli pominiesz `outputFilename`, Resgen.exe utworzy plik .resources o nazwie pliku głównego `inputFilename` w tym samym katalogu co `inputFilename`. Jeśli `outputFilename` zawiera ścieżkę katalogu, katalog musi istnieć.  
  
 Należy podać w pełni kwalifikowaną przestrzeń nazw dla pliku resources, określając ją w nazwie pliku i oddzielając od głównej nazwy plików kropką. Na przykład, `outputFilename` `MyCompany.Libraries.Strings.resources`jeśli jest , obszar nazw jest MyCompany.Libraries.  
  
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
  
 Ponadto można użyć programu Resgen.exe do konwersji osadzonych zasobów w zestawie .NET Framework na plik .resw— aplikacje ze Sklepu Windows 8.x.  
  
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
 Za pomocą `/compile` przełącznika można przekonwertować listę plików zasobów z jednego formatu na inny w ramach jednej operacji. Składnia jest następująca:  
  
```console  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Poniższe polecenie kompiluje trzy pliki, StringResources.txt, TableResources.resw i ImageResources.resw, do oddzielnych plików resources o nazwach StringResources.resources, TableResources.resources i ImageResources.resources.  
  
```console  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>
### <a name="exporting-resources-to-a-resw-file"></a>Eksportowanie zasobów do pliku resw  
 Jeśli tworzysz aplikację ze Sklepu Windows 8.x, możesz użyć zasobów z istniejącej aplikacji klasycznej. Jednak te dwa rodzaje aplikacji obsługują różne formaty plików. W aplikacjach komputerowych zasoby w plikach tekstowych (txt lub restex) lub w plikach resx są kompilowane do binarnych plików resources. W aplikacjach ze Sklepu Windows 8.x pliki .resw są kompilowane do plików binary package resource index (PRI). Program Resgen.exe umożliwia wypełnienie tej luki, wyodrębniając zasoby z pliku wykonywalnego lub zestawu satelickiego i zapisując je do jednego lub więcej plików .resw, które mogą być używane podczas tworzenia aplikacji ze Sklepu Windows 8.x.  
  
> [!IMPORTANT]
> Program Visual Studio automatycznie obsługuje wszystkie konwersje niezbędne do włączenia zasobów w przenośnej bibliotece do aplikacji ze Sklepu Windows 8.x. Używanie programu Resgen.exe bezpośrednio do konwersji zasobów w zestawie na format pliku resw jest interesujące tylko dla deweloperów, którzy chcą opracować aplikację ze Sklepu Windows 8.x poza programem Visual Studio.  
  
 Składnia służąca do generowania plików resw z zestawu jest następująca:  
  
```console  
resgen filename.extension  [outputDirectory]  
```  
  
 gdzie parametrami są:  
  
 `filename.extension`  
 Nazwa zestawu programu .NET Framework (plik wykonywalny lub biblioteka DLL). Jeśli plik nie zawiera żadnych zasobów, program Resgen.exe nie tworzy żadnych plików.  
  
 `outputDirectory`  
 Istniejący katalog, w którym mają zostać zapisane pliki resw. Jeśli `outputDirectory` zostanie pominięty, pliki .resw są zapisywane w bieżącym katalogu. Program Resgen.exe tworzy jeden plik resw dla każdego pliku resources w zestawie. Główna nazwa pliku resw jest taka sama jak główna nazwa pliku resources.  
  
 Poniższe polecenie tworzy plik resw w katalogu Win8Resources dla każdego pliku resources osadzonego w zestawie MyApp.exe:  
  
```console  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>
### <a name="conditionally-compiling-resources"></a>Warunkowe kompilowanie zasobów  
 Począwszy od programu .NET Framework 4.5, Program Resgen.exe obsługuje warunkową kompilację zasobów ciągów w plikach tekstowych (.txt i .restext). Dzięki temu można używać pojedynczego pliku zasobów w formacie tekstowym w wielu konfiguracjach kompilacji.  
  
 W pliku .txt lub .restext `#ifdef`należy użyć ...`#endif` konstrukcji, aby uwzględnić zasób w pliku binarnym .resources, jeśli symbol jest zdefiniowany, a użyto `#if !`... `#endif` konstrukcji, aby uwzględnić zasób, jeśli symbol nie jest zdefiniowany. W czasie kompilacji symbole można następnie `/define:` zdefiniować za pomocą opcji, po której następuje lista symboli rozdzielanych przecinkami. Porównanie jest rozróżniane z uwzględnieniem wielkości liter; przypadku symboli zdefiniowanych `/define` przez musi odpowiadać przypadku symboli w plikach tekstowych, które mają być skompilowane.  
  
 Na przykład następujący plik o nazwie UIResources.rext `AppTitle` zawiera zasób ciąg o nazwie, `PRODUCTION`który `CONSULT`może `RETAIL` przyjmować jedną z trzech wartości, w zależności od tego, czy symbole o nazwie , lub są zdefiniowane.  
  
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
  
 To polecenie utworzy plik resources zawierający dwa zasoby w postaci ciągów. Wartość zasobu `AppTitle` to "My Consulting Company Project Manager".  
  
<a name="Strong"></a>
### <a name="generating-a-strongly-typed-resource-class"></a>Generowanie silnie typizowanej klasy zasobów  
 Program Resgen.exe obsługuje silnie typizowane zasoby, które hermetyzują dostęp do zasobów przez tworzenie klas zawierających zestaw statycznych właściwości tylko do odczytu. Stanowi to alternatywę dla wywoływania metod <xref:System.Resources.ResourceManager> klasy bezpośrednio do pobierania zasobów. Można włączyć obsługę zasobów silnie typizowane za pomocą `/str` opcji w Resgen.exe, <xref:System.Resources.Tools.StronglyTypedResourceBuilder> która otacza funkcjonalność klasy. Po określeniu `/str` opcji dane wyjściowe Resgen.exe jest klasą, która zawiera silnie wpisane właściwości, które pasują do zasobów, do których odwołuje się parametr wejściowy. Ta klasa dostarcza silnie typizowany dostęp tylko do odczytu do zasobów, które są dostępne w przetwarzanym pliku.  
  
 Składania służąca do tworzenia silnie typizowanych zasobów jest następująca:  
  
```console  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry i przełączniki są następujące:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, dla którego należy wygenerować silnie typizowaną klasę zasobów. Plik może być plikiem tekstowym, plikiem w formacie XML lub binarnym plikiem resources; może mieć rozszerzenie txt, restext, resw lub resources.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. Jeśli `outputFilename` zawiera ścieżkę katalogu, katalog musi istnieć. Jeśli pominiesz `outputFilename`, Resgen.exe utworzy plik .resources o nazwie pliku głównego `inputFilename` w tym samym katalogu co `inputFilename`.  
  
 `outputFilename`może być plikiem tekstowym, opartym na języku XML lub binarnym .resources. Jeśli rozszerzenie pliku `outputFilename` różni się od `inputFilename`rozszerzenia pliku , Resgen.exe wykonuje konwersję pliku.  
  
 Jeśli `inputFilename` jest to plik .resources, program Resgen.exe `outputFilename` kopiuje plik .resources, jeśli jest również plikiem .resources. Jeśli `outputFilename` zostanie pominięty, resgen.exe `inputFilename` zastępuje identyczny plik .resources.  
  
 *language*  
 Język, w którym należy wygenerować kod źródłowy dla silnie typizowanej klasy zasobów. Możliwe wartości `cs` `C#`to `csharp` , i dla `vb` `visualbasic` kodu C# `vbs` i `vbscript` dla kodu języka `c++`Visual `mc`Basic `cpp` i kodu VBScript i , i , i dla kodu C++.  
  
 *Namespace*  
 Przestrzeń nazw zawierająca silnie typizowaną klasę zasobów. Plik resources i klasa zasobów powinny mieć taką samą przestrzeń nazw. Aby uzyskać informacje dotyczące określania `outputFilename`obszaru nazw w obszarze , zobacz [Kompilowanie zasobów do pliku binarnego](resgen-exe-resource-file-generator.md#Compiling). Jeśli *obszar nazw* zostanie pominięty, klasa zasobów nie jest zawarta w obszarze nazw.  
  
 *Classname*  
 Nazwa silnie typizowanej klasy zasobów. Powinna odpowiadać głównej nazwie pliku resources. Na przykład jeśli program Resgen.exe generuje plik resources o nazwie MyCompany.Libraries.Strings.resources, nazwa silnie typizowanej klasy zasobów to Strings. Jeśli *nazwa klasy* zostanie pominięta, wygenerowana klasa pochodzi `outputFilename`od nazwy głównej . Jeśli `outputFilename` zostanie pominięta, wygenerowana klasa pochodzi od `inputFilename`nazwy głównej .  
  
 *classname* nie może zawierać nieprawidłowych znaków, takich jak osadzone spacje. Jeśli *nazwa klasy* zawiera przestrzenie osadzone lub jeśli nazwa *klasy* jest generowana domyślnie z *inputFilename*, a *inputFilename* zawiera\_osadzone spacje, program Resgen.exe zastępuje wszystkie nieprawidłowe znaki podkreśleniem ( ).  
  
 *Pod nazwą*  
 Nazwa pliku klasy.  
  
 `/publicclass`  
 Sprawia, że silnie typizowane `internal` klasy zasobów publicznych, `Friend` a nie (w języku C#) lub (w języku Visual Basic). Dzięki temu zasoby będą dostępne spoza zestawu, w którym są osadzone.  
  
> [!IMPORTANT]
> Podczas tworzenia silnie typizowanej klasy zasobów nazwa pliku resources musi odpowiadać przestrzeni nazw i nazwie klasy generowanego kodu. Jednak program Resgen.exe umożliwia określenie opcji, które tworzą plik resources mający niezgodną nazwę. Aby obejść ten problem, należy zmienić nazwę pliku wyjściowego po jego wygenerowaniu.  
  
 Silnie typizowana klasa zasobów ma następujące składowe:  
  
- Konstruktor bez parametrów, który może służyć do tworzenia wystąpienia klasy zasobów silnie typizowane.  
  
- A `static` (C#) `Shared` lub (Visual Basic) `ResourceManager` i tylko <xref:System.Resources.ResourceManager> do odczytu właściwości, która zwraca wystąpienie, które zarządza silnie typią zasób.  
  
- Właściwość `Culture` statyczna, która umożliwia ustawienie kultury używanej do pobierania zasobów. Domyślnie jego wartość `null`jest , co oznacza, że używana jest bieżąca kultura interfejsu użytkownika.  
  
- Jeden `static` (C#) `Shared` lub (Visual Basic) i właściwość tylko do odczytu dla każdego zasobu w pliku .resources. Nazwa właściwości to nazwa zasobu.  
  
 Na przykład następujące polecenie kompiluje plik zasobu o nazwie StringResources.txt w StringResources.resources i generuje klasę o nazwie `StringResources` w pliku kodu źródłowego języka Visual Basic o nazwie StringResources.vb, który może służyć do uzyskiwania dostępu do Menedżera zasobów.  
  
```console  
resgen StringResources.txt /str:vb,,StringResources
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Zasoby w aplikacjach klasycznych](../resources/index.md)
- [Tworzenie plików zasobów](../resources/creating-resource-files-for-desktop-apps.md)
- [Al.exe (konsolidator zestawów)](al-exe-assembly-linker.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
