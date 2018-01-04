---
title: "Resgen.exe (Generator pliku zasobów)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "46"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca54817183b5e659b62ef04b1693698bd689370b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="resgenexe-resource-file-generator"></a>Resgen.exe (Generator pliku zasobów)
Generator plików zasobów (Resgen.exe) konwertuje pliki tekstowe (txt lub restext) i pliki zasobów w formacie XML (resx) na pliki binarne (resources) środowiska uruchomieniowego języka wspólnego, które można osadzić w binarnym pliku wykonywalnym środowiska uruchomieniowego lub zestawie satelickim. (Zobacz [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).)  
  
 Program Resgen.exe to uniwersalne narzędzie do konwersji zasobów, które wykonuje następujące zadania:  
  
-   Konwertuje pliki txt lub restext na pliki resx lub resources. (Format plików restext jest identyczny z formatem plików txt. Jednak rozszerzenie restext pomaga łatwiej zidentyfikować pliki tekstowe, które zawierają definicje zasobów).  
  
-   Konwertuje pliki resources na pliki tekstowe lub resx.  
  
-   Konwertuje pliki resx na pliki tekstowe lub resources.  
  
-   Wyodrębnia zasobów ciągu z zestawu do pliku .resw, które jest odpowiednie do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
-   Tworzy silnie typizowaną klasę, która zapewnia dostęp do poszczególnych zasobów o nazwie oraz na <xref:System.Resources.ResourceManager> wystąpienia.  
  
 Jeśli działanie programu Resgen.exe kończy się niepowodzeniem z dowolnej przyczyny, zwracaną wartością jest -1.  
  
 Aby uzyskać pomoc dotyczącą programu Resgen.exe, należy użyć następującego polecenia, bez określania żadnych opcji, w celu wyświetlenia składni polecenia i opcji programu Resgen.exe:  
  
```  
resgen  
```  
  
 Można również użyć `/?` przełącznika:  
  
```  
resgen /?  
```  
  
 Jeśli używasz Resgen, exe generuje pliki binarne .resources, kompilator języka umożliwia osadzanie plików binarnych w pliku wykonywalnego zestawów lub można użyć [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do kompilowania ich do zestawów satelickich.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
resgen  [/define:symbol1[,symbol2,...]] [/useSourcePath] filename.extension  | /compile filename.extension... [outputFilename.extension] [/r:assembly] [/str:lang[,namespace[,class[,file]]] [/publicclass]]   
```  
  
```  
resgen filename.extension [outputDirectory]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr lub opcja|Opis|  
|-------------------------|-----------------|  
|`/define:`*symbol1*[, *symbol2*,...]|Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], obsługuje kompilacja warunkowa w tekstowy (txt lub .restext) plików zasobów. Jeśli *symbol* odpowiada symbol zawarty w pliku wejściowego tekstu w `#ifdef` konstrukcji, zasobu ciągu skojarzona jest uwzględniona w pliku .resources. Jeśli plik wejściowy tekst zawiera `#if !` instrukcji przy użyciu symbolu, który nie jest zdefiniowany przez `/define` przełącznika, zasobu ciągu skojarzona jest uwzględniona w pliku zasobów.<br /><br /> `/define`jest ignorowana, jeśli jest używana z plików z systemem innym niż tekstu. W symbolach jest uwzględniania wielkość liter.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [warunkowo kompilowanie zasobów](#Conditional) dalszej części tego tematu.|  
|`useSourcePath`|Określa, że bieżący katalog pliku wejściowego ma być używany na potrzeby rozpoznawania względnych ścieżek plików.|  
|`/compile`|Umożliwia określenie wielu plików tekstowych lub resx w celu konwersji na wiele plików resources w pojedynczej zbiorczej operacji. Jeśli ta opcja nie jest określona, można określić tylko jeden argument pliku wejściowego. Pliki wyjściowe są nazywane *filename*.resources.<br /><br /> Nie można użyć tej opcji z `/str:` opcji.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [kompilowanie lub Konwersja wielu plików](#Multiple) dalszej części tego tematu.|  
|`/r:``assembly`|Odwołuje się do metadanych z określonego zestawu. Jest używana podczas konwersji plików resx i zezwala programowi Resgen.exe na serializację lub deserializację zasobów obiektu. Jest on podobny do `/reference:` lub `/r:` opcje Kompilatory języka C# i Visual Basic.|  
|`filename.extension`|Określa nazwę pliku wejściowego do konwersji. Jeśli używasz składni wiersza polecenia po pierwsze, dłuższy przedstawione przed tej tabeli `extension` musi mieć jedną z następujących czynności:<br /><br /> .txt lub .restext<br /> Plik tekstowy do konwersji na plik resources lub resx. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów. Aby uzyskać informacje o formacie pliku, zobacz sekcję "Zasobów w plikach tekstowych" [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).<br /><br /> .resx<br /> Plik zasobów w języku XML do konwersji na plik .resources lub plik tekstowy (txt lub restext).<br /><br /> .resources<br /> Plik binarny zasobów do konwersji na plik resx lub plik tekstowy (txt lub restext).<br /><br /> Jeśli używasz drugiej, krótszą składni wiersza polecenia przedstawionych przed tej tabeli `extension` musi być następujące:<br /><br /> .exe lub .dll<br /> Zestawu .NET Framework (plik wykonywalny lub biblioteka) są którego zasoby ciągu do wyodrębnienia w pliku .resw do użytku w opracowywaniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.|  
|`outputFilename.extension`|Określa nazwę i typ tworzonego pliku zasobów.<br /><br /> Ten argument jest opcjonalny podczas konwersji z pliku txt, restext lub resx na plik resources. Jeśli nie określisz `outputFilename`, Resgen.exe dołącza rozszerzeniem .resources w danych wejściowych `filename` i zapisuje plik w katalogu, który zawiera `filename,extension`.<br /><br /> `outputFilename.extension` Argumentu jest wymagany, jeśli konwersja z plik .resources. Określa nazwę pliku z rozszerzeniem resx podczas konwersji pliku resources na plik zasobów w formacie XML. Określa nazwę pliku z rozszerzeniem txt lub restext podczas konwersji na plik resources lub plik tekstowy. Plik resources należy konwertować na plik txt tylko wtedy, gdy plik resources zawiera wyłącznie wartości w postaci ciągów.|  
|`outputDirectory`|Dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji Określa katalog, w którym .resw plik, który zawiera zasoby ciągów w `filename.extension` zostanie zapisany. `outputDirectory`musi już istnieć.|  
|`/str:``language[,namespace[,classname[,filename]]]`|Tworzy plik klasy zasobu o jednoznacznie w języku programowania określone w `language` opcji. `language`może składać się z jednego z następujących literały:<br /><br /> — Dla C#: `c#`, `cs`, lub `csharp`.<br />— W języku Visual Basic: `vb` lub `visualbasic`.<br />— Dla VBScript: `vbs` lub `vbscript`.<br />— Dla języka C++: `c++`, `mc`, lub `cpp`.<br />— Dla języka JavaScript: `js`, `jscript`, lub `javascript`.<br /><br /> `namespace` Opcja określa domyślną przestrzeń nazw projektu, `classname` opcji Nazwa wygenerowanej klasy i `filename` opcja określa nazwę pliku klasy.<br /><br /> `/str:` Opcja umożliwia tylko jeden plik wejściowy, więc nie można używać z `/compile` opcji.<br /><br /> Jeśli `namespace` jest określony, ale `classname` nie jest nazwa klasy jest pochodną nazwę pliku wyjściowego (na przykład, znaki podkreślenia są zastępowane dla okresów). Zasoby silnie typizowane mogą nie działać poprawnie jako wynik. Aby tego uniknąć, należy określić zarówno nazwę klasy, jak i nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji na temat tej opcji, zobacz [generowania silnie Typizowanej klasę zasobu o](#Strong) dalszej części tego tematu.|  
|`/publicClass`|Tworzy silnie typizowaną klasę zasobu jako klasę publiczną. Domyślnie klasa zasobów jest `internal` w języku C# i `Friend` w języku Visual Basic.<br /><br /> Ta opcja jest ignorowana, jeśli `/str:` opcja nie jest używana.|  
  
## <a name="resgenexe-and-resource-file-types"></a>Program Resgen.exe i typy plików zasobów  
 Aby program Resgen.exe mógł pomyślnie konwertować zasoby, pliki tekstowe i resx muszą mieć poprawny format.  
  
### <a name="text-txt-and-restext-files"></a>Pliki tekstowe (txt i restext)  
 Pliki tekstowe (txt lub restext) mogą zawierać tylko zasoby w postaci ciągów. Zasoby w postaci ciągów są przydatne podczas pisania aplikacji, która musi być przetłumaczona na kilka języków. Na przykład można łatwo poddać regionalizacji napisy w menu przy użyciu odpowiedniego zasobu w postaci ciągu. Program Resgen.exe odczytuje pliki tekstowe, które zawierają pary nazwa/wartość, gdzie nazwa jest ciągiem opisującym zasób, a wartość to właśnie ciąg zasobu.  
  
> [!NOTE]
>  Aby uzyskać informacje o formacie plików txt i .restext, zobacz sekcję "Zasobów w plikach tekstowych" [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Plik tekstowy, który zawiera zasoby, musi być zapisany z użyciem kodowania UTF-8 lub Unicode (UTF-16), chyba że zawiera tylko znaki z zakresu Łaciński podstawowy (do U+007F). Program Resgen.exe usuwa rozszerzone znaki ANSI podczas przetwarzania pliku tekstowego, który został zapisany przy użyciu kodowania ANSI.  
  
 Program Resgen.exe sprawdza, czy plik tekstowy zawiera zduplikowane nazwy zasobów. Jeśli plik tekstowy zawiera zduplikowane nazwy zasobów, program Resgen.exe wyświetli ostrzeżenie i zignoruje drugą wartość.  
  
### <a name="resx-files"></a>Pliki resx  
 Format plików zasobów resx składa się z wpisów XML. Można określić zasoby w postaci ciągów w tych wpisach XML, tak jak w plikach tekstowych. Główną zaletą plików resx w porównaniu z plikami tekstowymi jest to, że można określić lub osadzić w nich obiekty. Podczas przeglądania pliku resx można zobaczyć binarną formę osadzonego obiektu (na przykład obrazka), gdy te informacje binarne są częścią manifestu zasobu. Tak jak w przypadku plików tekstowych, plik resx można otworzyć za pomocą edytora tekstów (takiego jak Notatnik lub program Microsoft Word), a następnie można pisać i analizować jego zawartość, a także wykonywać na niej różne operacje. Należy zauważyć, że wymaga to dobrej znajomości tagów XML i struktury pliku resx. Aby uzyskać więcej informacji o formacie pliku .resx, zobacz sekcję "Zasoby w plikach resx" [tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
 Aby utworzyć plik .resources, który zawiera obiekty typu osadzonego, musi użyć Resgen.exe do konwertowania pliku .resx zawierających obiekty albo Dodaj zasoby obiektu do pliku bezpośrednio z kodu przez wywołanie metody udostępniane przez <xref:System.Resources.ResourceWriter> Klasa.  
  
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
 Resgen.exe można użyć w różnych sposobów: Aby skompilować plik tekstowy lub opartych na języku XML zasobów do pliku binarnego, aby konwertowanie formatów plików zasobów, a także do generowania klasy, która opakowuje <xref:System.Resources.ResourceManager> funkcji i zapewnia dostęp do zasobów. Ta sekcja zawiera szczegółowe informacje dotyczące każdego zadania:  
  
-   [Kompilowanie zasobów do pliku binarnego](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling)  
  
-   [Konwertowanie typów plików zasobów](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Convert)  
  
-   [Kompilowanie lub Konwersja wielu plików](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Multiple)  
  
-   [Eksportowanie zasobów do plików resw](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Exporting)  
  
-   [Kompilowanie warunkowe zasobów](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Conditional)  
  
-   [Generowanie klasy zasobu o jednoznacznie](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Strong)  
  
<a name="Compiling"></a>   
### <a name="compiling-resources-into-a-binary-file"></a>Kompilowanie zasobów do pliku binarnego  
 Najbardziej powszechnym zastosowaniem programu Resgen.exe jest kompilacja pliku zasobów w formacie tekstowym (pliku txt lub restext) lub w formacie XML (pliku resx) do pliku binarnego resources. Plik wyjściowy następnie mogą być osadzone w zestawie głównym przez kompilator języka lub w zestawie satelickim przez [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
 Składnia służąca do kompilacji pliku zasobów jest następująca:  
  
```  
resgen inputFilename [outputFilename]   
```  
  
 gdzie parametrami są:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, który należy skompilować. Program Resgen.exe kompiluje tylko pliki z rozszerzeniem txt, restext lub resx.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. W przypadku pominięcia `outputFilename`, przy użyciu nazwy pliku głównego Resgen.exe utworzy plik .resources `inputFilename` w tym samym katalogu co `inputFilename`. Jeśli `outputFilename` zawiera ścieżkę katalogu ten katalog musi istnieć.  
  
 Należy podać w pełni kwalifikowaną przestrzeń nazw dla pliku resources, określając ją w nazwie pliku i oddzielając od głównej nazwy plików kropką. Na przykład jeśli `outputFilename` jest `MyCompany.Libraries.Strings.resources`, przestrzeń nazw jest MyCompany.Libraries.  
  
 Poniższe polecenie odczytuje pary nazwa/wartość z pliku Resources.txt i zapisuje w binarnym pliku resources o nazwie Resources.resources. Nazwa pliku wyjściowego nie jest jawnie określona, więc domyślnie plik wyjściowy otrzymuje taką samą nazwę jak plik wejściowy.  
  
```  
resgen Resources.txt   
```  
  
 Poniższe polecenie odczytuje pary nazwa/wartość z pliku Resources.restext i zapisuje w binarnym pliku zasobów o nazwie StringResources.resources.  
  
```  
resgen Resources.restext StringResources.resources  
```  
  
 Poniższe polecenie odczytuje plik wejściowy w formacie XML o nazwie Resources.resx i zapisuje plik binarny resources o nazwie Resources.resources.  
  
```  
resgen Resources.resx Resources.resources  
```  
  
<a name="Convert"></a>   
### <a name="converting-between-resource-file-types"></a>Konwertowanie między typami plików zasobów  
 Oprócz kompilowania plików zasobów w formacie tekstowym lub XML do plików binarnych resources, program Resgen.exe może przekonwertować dowolny obsługiwany typ pliku na dowolny inny obsługiwany typ. Oznacza to, że można wykonywać następujące konwersje:  
  
-   Pliki txt i restext na pliki resx.  
  
-   Pliki resx na pliki txt i restext.  
  
-   Pliki resources na pliki txt i restext.  
  
-   Pliki resources na pliki resx.  
  
 Składnia jest taka sama, jak pokazana w poprzedniej sekcji.  
  
 Ponadto można użyć Resgen.exe przekonwertować zasoby osadzone w zestawie .NET Framework na tor plików resw [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Poniższe polecenie odczytuje binarny plik zasobów Resources.resources i zapisuje plik wyjściowy w formacie XML o nazwie Resources.resx.  
  
```  
resgen Resources.resources Resources.resx  
```  
  
 Poniższe polecenie odczytuje plik zasobów w formacie tekstowym o nazwie StringResources.txt i zapisuje plik zasobów w formacie XML o nazwie LibraryResources.resx. Ponadto pliku resx można użyć, oprócz przechowywania zasobów w postaci ciągów, do przechowywania zasobów niebędących ciągami.  
  
```  
resgen StringResources.txt LibraryResources.resx  
```  
  
 Poniższe dwa polecenia odczytują plik zasobów w formacie XML o nazwie Resources.resx i zapisują pliki tekstowe o nazwach Resources.txt i Resources.restext. Należy zauważyć, że jeżeli plik resx zawiera jakiekolwiek obiekty osadzone, nie zostaną one dokładnie przekonwertowane na pliki tekstowe.  
  
```  
resgen Resources.resx Resources.txt  
resgen Resources.resx Resources.restext  
```  
  
<a name="Multiple"></a>   
### <a name="compiling-or-converting-multiple-files"></a>Kompilowanie lub konwertowanie wielu plików  
 Można użyć `/compile` przełącznik, aby przekonwertować lista plików zasobów z jednego formatu na inny w ramach jednej operacji. Składnia jest następująca:  
  
```  
resgen /compile filename.extension [filename.extension...]  
```  
  
 Poniższe polecenie kompiluje trzy pliki, StringResources.txt, TableResources.resw i ImageResources.resw, do oddzielnych plików resources o nazwach StringResources.resources, TableResources.resources i ImageResources.resources.  
  
```  
resgen /compile StringResources.txt TableResources.resx ImageResources.resx  
```  
  
<a name="Exporting"></a>   
### <a name="exporting-resources-to-a-resw-file"></a>Eksportowanie zasobów do pliku resw  
 Jeśli projektujesz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, można korzystać z zasobów z istniejącej aplikacji klasycznych. Jednak te dwa rodzaje aplikacji obsługują różne formaty plików. W aplikacjach komputerowych zasoby w plikach tekstowych (txt lub restex) lub w plikach resx są kompilowane do binarnych plików resources. W [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, plików .resw są kompilowane do plików indeksu (PRI) zasobów binarnych pakietu. Resgen.exe umożliwia rozbieżność wyodrębnianie zasobów z pliku wykonywalnego lub zestawu satelickiego i zapisaniu ich do jednego lub więcej plików resw, które mogą być używane podczas tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
> [!IMPORTANT]
>  Visual Studio automatycznie obsługuje wszystkie konwersje niezbędne do włączania zasoby przenośnej biblioteki do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Przy użyciu Resgen.exe bezpośrednio do przekonwertowania zasobów w zestawie na .resw format pliku ma znaczenie tylko dla deweloperów, którzy chcą tworzyć [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji poza Visual Studio.  
  
 Składnia służąca do generowania plików resw z zestawu jest następująca:  
  
```  
resgen filename.extension  [outputDirectory]  
```  
  
 gdzie parametrami są:  
  
 `filename.extension`  
 Nazwa zestawu programu .NET Framework (plik wykonywalny lub biblioteka DLL). Jeśli plik nie zawiera żadnych zasobów, program Resgen.exe nie tworzy żadnych plików.  
  
 `outputDirectory`  
 Istniejący katalog, w którym mają zostać zapisane pliki resw. Jeśli `outputDirectory` jest pominięty, pobieranie plików .resw są zapisywane w bieżącym katalogu. Program Resgen.exe tworzy jeden plik resw dla każdego pliku resources w zestawie. Główna nazwa pliku resw jest taka sama jak główna nazwa pliku resources.  
  
 Poniższe polecenie tworzy plik resw w katalogu Win8Resources dla każdego pliku resources osadzonego w zestawie MyApp.exe:  
  
```  
resgen MyApp.exe Win8Resources  
```  
  
<a name="Conditional"></a>   
### <a name="conditionally-compiling-resources"></a>Warunkowe kompilowanie zasobów  
 Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Resgen.exe obsługuje kompilacja warunkowa zasobów ciągu w plikach tekstowych (txt i .restext). Dzięki temu można używać pojedynczego pliku zasobów w formacie tekstowym w wielu konfiguracjach kompilacji.  
  
 W pliku txt lub .restext używasz `#ifdef`...`#endif` konstrukcja do uwzględnienia w pliku binarnego .resources zasobu, jeśli symbol jest zdefiniowana i używana będzie `#if !`... `#endif` konstrukcji, aby uwzględnić zasobu, jeśli nie zdefiniowano symbolu. W czasie kompilacji, następnie zdefiniuj symboli za pomocą `/define:` opcji następuje rozdzielana przecinkami lista symboli. Wynik porównania ma prawidłową wielkość liter; w przypadku symboli zdefiniowanych przez `/define` muszą odpowiadać symboli w plikach tekstowych, które ma być kompilowana.  
  
 Na przykład następujący plik o nazwie UIResources.rext zawiera zasób ciągu o nazwie `AppTitle` który można wykonać jedną z trzech wartości, w zależności od tego, czy o nazwie symbole `PRODUCTION`, `CONSULT`, lub `RETAIL` są zdefiniowane.  
  
```  
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
  
```  
resgen /define:CONSULT UIResources.restext  
```  
  
 To polecenie utworzy plik resources zawierający dwa zasoby w postaci ciągów. Wartość `AppTitle` zasób jest "Moje konsultacji projektu Menedżer firmy".  
  
<a name="Strong"></a>   
### <a name="generating-a-strongly-typed-resource-class"></a>Generowanie silnie typizowanej klasy zasobów  
 Program Resgen.exe obsługuje silnie typizowane zasoby, które hermetyzują dostęp do zasobów przez tworzenie klas zawierających zestaw statycznych właściwości tylko do odczytu. Zapewnia to alternatywę do wywoływania metody <xref:System.Resources.ResourceManager> klasy bezpośrednio do pobierania zasobów. Można włączyć obsługę zasobu o jednoznacznie przy użyciu `/str` opcji w Resgen.exe, który opakowuje funkcjonalność <xref:System.Resources.Tools.StronglyTypedResourceBuilder> klasy. Po określeniu `/str` opcja, dane wyjściowe programu Resgen.exe jest klasa, która zawiera jednoznacznie właściwości, które odpowiada zasoby, do których odwołuje się parametr wejściowy. Ta klasa dostarcza silnie typizowany dostęp tylko do odczytu do zasobów, które są dostępne w przetwarzanym pliku.  
  
 Składania służąca do tworzenia silnie typizowanych zasobów jest następująca:  
  
```  
resgen inputFilename [outputFilename] /str:language[,namespace,[classname[,filename]]] [/publicClass]  
```  
  
 Parametry i przełączniki są następujące:  
  
 `inputFilename`  
 Nazwa pliku zasobów, łącznie z rozszerzeniem, dla którego należy wygenerować silnie typizowaną klasę zasobów. Plik może być plikiem tekstowym, plikiem w formacie XML lub binarnym plikiem resources; może mieć rozszerzenie txt, restext, resw lub resources.  
  
 `outputFilename`  
 Nazwa pliku wyjściowego. Jeśli `outputFilename` zawiera ścieżkę katalogu ten katalog musi istnieć. W przypadku pominięcia `outputFilename`, przy użyciu nazwy pliku głównego Resgen.exe utworzy plik .resources `inputFilename` w tym samym katalogu co `inputFilename`.  
  
 `outputFilename`może to być plik tekstowy, opartych na języku XML lub binarne .resources. Jeśli rozszerzenie pliku `outputFilename` różni się od rozszerzenie pliku `inputFilename`, Resgen.exe wykonuje konwersję pliku.  
  
 Jeśli `inputFilename` plik .resources, plik .resources, jeśli kopie Resgen.exe `outputFilename` jest również plik .resources. Jeśli `outputFilename` jest pominięty, zastępuje Resgen.exe `inputFilename` przy użyciu pliku .resources identyczne.  
  
 *język*  
 Język, w którym należy wygenerować kod źródłowy dla silnie typizowanej klasy zasobów. Możliwe wartości to `cs`, `C#`, i `csharp` dla kodu C#, `vb` i `visualbasic` kodu języka Visual Basic `vbs` i `vbscript` dla kod VBScript i `c++`, `mc`i `cpp` dla kodu C++.  
  
 *namespace*  
 Przestrzeń nazw zawierająca silnie typizowaną klasę zasobów. Plik resources i klasa zasobów powinny mieć taką samą przestrzeń nazw. Informacji o określaniu przestrzeń nazw w `outputFilename`, zobacz [kompilowanie zasobów do pliku binarnego](../../../docs/framework/tools/resgen-exe-resource-file-generator.md#Compiling). Jeśli *przestrzeni nazw* jest pominięty, klasa zasobów nie znajduje się w przestrzeni nazw.  
  
 *ClassName*  
 Nazwa silnie typizowanej klasy zasobów. Powinna odpowiadać głównej nazwie pliku resources. Na przykład jeśli program Resgen.exe generuje plik resources o nazwie MyCompany.Libraries.Strings.resources, nazwa silnie typizowanej klasy zasobów to Strings. Jeśli *classname* jest pominięty, wygenerowana klasa pochodzi od nazwy głównego `outputFilename`. Jeśli `outputFilename` jest pominięty, wygenerowana klasa pochodzi od nazwy głównego `inputFilename`.  
  
 *ClassName* nie może zawierać nieprawidłowych znaków takich jak osadzonych spacji. Jeśli *classname* zawiera spacje, lub jeśli *classname* jest generowany przez domyślne *inputFilename*, i *inputFilename* zawiera spacje, Resgen.exe zastępuje wszystkie nieprawidłowe znaki podkreślenia (_).  
  
 *Nazwa pliku*  
 Nazwa pliku klasy.  
  
 `/publicclass`  
 Udostępnia klasę zasobu o jednoznacznie publicznie zamiast `internal` (w języku C#) lub `Friend` (w języku Visual Basic). Dzięki temu zasoby będą dostępne spoza zestawu, w którym są osadzone.  
  
> [!IMPORTANT]
>  Podczas tworzenia silnie typizowanej klasy zasobów nazwa pliku resources musi odpowiadać przestrzeni nazw i nazwie klasy generowanego kodu. Jednak program Resgen.exe umożliwia określenie opcji, które tworzą plik resources mający niezgodną nazwę. Aby obejść ten problem, należy zmienić nazwę pliku wyjściowego po jego wygenerowaniu.  
  
 Silnie typizowana klasa zasobów ma następujące składowe:  
  
-   Konstruktor bez parametrów, którego można użyć do utworzenia wystąpienia silnie typizowanej klasy zasobów.  
  
-   A `static` (C#) lub `Shared` (Visual Basic) i tylko do odczytu `ResourceManager` właściwość, która zwraca <xref:System.Resources.ResourceManager> wystąpienia, która zarządza zasobu o jednoznacznie.  
  
-   Statycznego `Culture` właściwość, która umożliwia określenie kultury użyte do pobierania zasobów. Domyślnie, jego wartość wynosi `null`, co oznacza, że służy bieżącej kultury interfejsu użytkownika.  
  
-   Jeden `static` (C#) lub `Shared` (Visual Basic), a właściwość tylko do odczytu dla każdego zasobu w pliku .resources. Nazwa właściwości to nazwa zasobu.  
  
 Na przykład poniższe polecenie kompiluje plik zasobów o nazwie StringResources.txt StringResources.resources i generuje klasę o nazwie `StringResources` w źródle Visual Basic pliku kodu o nazwie StringResources.vb, którego można uzyskać dostęp do zasobu Menedżer.  
  
```  
resgen StringResources.txt /str:vb,,StringResources   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Zasoby w aplikacjach klasycznych](../../../docs/framework/resources/index.md)  
 [Tworzenie plików zasobów](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
