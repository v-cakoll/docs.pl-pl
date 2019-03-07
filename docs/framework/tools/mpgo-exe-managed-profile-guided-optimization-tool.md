---
title: Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20b4df2a663bdc584b5f350c95c8c533f1cc7c8e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496823"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)

Z przewodnikiem narzędzia optymalizacji zarządzanym profilem (Mpgo.exe) jest narzędziem wiersza polecenia, które używa typowych scenariuszy użytkownika końcowego do optymalizacji zestawów obrazu natywnego, które są tworzone przez [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). To narzędzie umożliwia uruchamianie scenariuszy szkoleniowych, które generują dane profilu. [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) używa tych danych do optymalizacji jego zestawów aplikacji obrazu natywnego wygenerowanego. Scenariusz szkoleniowy jest próbnym uruchomieniem oczekiwanego użycia aplikacji. Mpgo.exe jest dostępny w programie Visual Studio Ultimate 2012 i jego nowszych wersjach. Począwszy od programu Visual Studio 2013 umożliwia także Mpgo.exe zoptymalizować [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
Profilowana optymalizacja poprawia czas uruchamiania aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepustowość przez zbieranie danych ze scenariuszy szkoleniowych i używanie ich do optymalizowania układu obrazów natywnych.  
  
Jeśli wystąpią problemy z wydajnością czasu uruchamiania i rozmiarem zestawu roboczego dla zestawów języka pośredniego (IL), zaleca się użyć w pierwszej kolejności Ngen.exe, aby wyeliminować koszty kompilacji JIT oraz umożliwić udostępnianie kodu. Jeśli potrzebujesz dodatkowych usprawnień, możesz użyć Mpgo.exe do dalszej optymalizacji aplikacji. Dane dotyczące wydajności z zestawów niezoptymalizowanego obrazu natywnego można zastosować jako podstawę do oszacowania wzrostu wydajności. Użycie Mpgo.exe może spowodować przyspieszenie zimnego uruchamiania i zmniejszenie rozmiaru zestawu roboczego. Mpgo.exe dodaje informacje do zestawów IL, których Ngen.exe używa do tworzenia zoptymalizowanych zestawów obrazu natywnego. Aby uzyskać więcej informacji, zobacz wpis [zwiększanie wydajności uruchamiania aplikacji dla pulpitu](https://go.microsoft.com/fwlink/p/?LinkId=248943) w blogu .NET.  
  
To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dla deweloperów programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7) z poświadczeniami administratora i wpisz następujące polecenie w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
W przypadku aplikacji klasycznych:  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Aby uzyskać [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji:  
  
## <a name="syntax"></a>Składnia  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametry  
 We wszystkich argumentach programu Mpgo.exe nie jest rozróżniana wielkość liter. Polecenia są poprzedzone kreską.  
  
> [!NOTE]
> Można użyć dowolnego `–Scenario` lub `–Import` jako wymaganego polecenia, ale nie oba. Brak wymaganych parametrów są używane w przypadku określenia `–Reset` opcji.

|Wymagany parametr|Opis|
|------------------------|-----------------|
|`-Scenario` \<*Polecenie*><br /><br /> —lub—<br /><br /> `-Scenario` \<*packageName*><br /><br /> —lub—<br /><br /> `-Import` \<*directory*>|W przypadku aplikacji klasycznych użyj `–Scenario` Aby określić polecenie do uruchomienia aplikacji, chcesz zoptymalizować, włączając żadnych argumentów wiersza polecenia. Użyj trzech zestawów znaków cudzysłowu wokół *polecenia* Jeśli Określa on ścieżkę zawierającą spacje; na przykład: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Nie należy używać znaków cudzysłowu podwójnego; nie będą one działać prawidłowo Jeśli *polecenia* zawiera spacje.<br /><br /> —lub—<br /><br /> Aby uzyskać [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] , korzystają `–Scenario` Aby określić pakiet, który chcesz wygenerować informację o profilu. Jeśli określisz nazwę wyświetlaną pakietu lub nazwę rodziny pakietów zamiast pełnej nazwy pakietu, Mpgo.exe wybierze pakiet, który pasuje do podanej nazwy, pod warunkiem, że istnieje tylko jedno dopasowanie. Jeśli kilka pakietów odpowiada określonej nazwie, Mpgo.exe wyświetli monit o wybrania pakietu.<br /><br /> —lub—<br /><br /> Użyj `-Import` do określenia tej optymalizacji danych z poprzednio zoptymalizowanych zestawów powinny służyć do optymalizowania zestawów na liście `-AssemblyList`. *katalog* Określa katalog zawierający poprzednio zoptymalizowane pliki. Zestawy określone w `–AssemblyList` lub `–AssemblyListFile` są nowymi wersjami zestawów do zoptymalizowania przy użyciu danych z zaimportowanych plików. Używanie danych optymalizacji ze starszych wersji zestawów pozwala zoptymalizować nowsze wersje zestawów bez ponownego uruchamiania scenariusza.  Jednakże, jeśli zaimportowany i docelowy zestaw zawierają znacznie różniący się kod, dane optymalizacji będą nieskuteczne. Nazwy zestawów określonych w `–AssemblyList` lub `–AssemblyListFile` musi znajdować się w katalogu określonym przez `–Import` *katalogu*. Użyj trzech zestawów znaków cudzysłowu wokół *katalogu* Jeśli Określa on ścieżkę zawierającą spacje.<br /><br /> Należy określić `–Scenario` lub `–Import`, ale nie oba parametry.|
|`-OutDir` \<*directory*>|Katalog, w którym będą umieszczone zoptymalizowane zestawy. Jeśli zestaw już istnieje w folderze katalogu wyjściowego, tworzona jest nowa kopia i numer indeksu jest dołączany do nazwy; na przykład: *assemblyname*-1.exe. Użyj podwójnego cudzysłowu *katalogu* Jeśli Określa on ścieżkę zawierającą spacje.|
|`-AssemblyList` \<*assembly1 assembly2...*><br /><br /> —lub—<br /><br /> `-AssemblyListFile` \<*file*>|Lista zestawów (w tym pliki exe i dll) rozdzielonych spacjami, dla których chcesz zbierać informacje profilowe. Można określić `C:\Dir\*.dll` lub `*.dll` aby wybrać wszystkie zestawy w wyznaczonym lub bieżącym katalogu roboczym. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.<br /><br /> —lub—<br /><br /> Plik tekstowy, który zawiera listę zestawów, dla których chcesz zebrać informacje o profilu. W każdym wierszu wymieniony jest jeden zestaw. Jeśli nazwa zestawu rozpoczyna się łącznikiem (-), użyj listy plików zestawów lub zmień nazwę zestawu.|
|`-AppID` \<*appId*>|Identyfikator aplikacji w określonym pakiecie. Jeśli używasz symbolu wieloznacznego (\*), Mpgo.exe spróbuje wyliczyć identyfikatory AppID w pakiecie i powróci do \< *package_family_name*>! Aplikacja, jeśli zakończy się niepowodzeniem. Jeżeli określono ciąg, który jest poprzedzony znakiem wykrzyknika (!), Mpgo.exe będzie łączyć nazwę rodziny pakietu z dostarczonym argumentem.|
|`-Timeout` \<*sekundy*>|Ilość czasu, aby umożliwić [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji do uruchomienia przed zakończeniem aplikacji.|

|Parametr opcjonalny|Opis|
|------------------------|-----------------|
|`-64bit`|Instrumentuje zestawy do systemów 64-bitowych.  Nawet jeśli zestaw jest zadeklarowany jako 64-bitowy, należy określić ten parametr dla zestawów 64-bitowych.|
|`-ExeConfig` \<*Nazwa pliku*>|Określa plik konfiguracji używany przez scenariusz do określenia informacje o wersji i module ładującym.|
|`-f`|Wymusza umieszczenie danych profilu w zestawie binarnym, nawet jeśli jest podpisany.  Jeśli zestaw jest podpisany, musi zostać ponownie podpisany; w przeciwnym razie zestawu nie będzie można załadować i uruchomić.|
|`-Reset`|Resetuje środowisko, aby była pewność, że przerwane sesje profilowania nie mają wpływu na swoje zestawy, a następnie kończy działanie. Środowisko jest resetowane domyślnie przed i po sesji profilowania.|
|`-Timeout` \<*czas w sekundach*>|Określa czas profilowania w sekundach. Użyj wartości, która jest nieco większa niż obserwowane czasy uruchamiania aplikacji GUI. Na koniec limitu czasu dane profilu są rejestrowana, mimo że aplikacja kontynuuje działanie. Jeśli ta opcja nie zostanie ustawiona, profilowanie będzie kontynuowane do czasu zamknięcia aplikacji, w czasie którym dane będą rejestrowane.|
|`-LeaveNativeImages`|Określa, że zinstrumentowane obrazy natywne nie powinny zostać usunięte po uruchomieniu tego scenariusza. Ta opcja jest używana przede wszystkim, gdy uzyskujesz aplikację, którą określono dla działającego scenariusza. Uniemożliwi to odtworzenie obrazów natywnych dla kolejnych uruchomień Mpgo.exe. W przypadku użycia tej opcji opcję w pamięci podręcznej po zakończeniu działania aplikacji mogą znajdować się oddzielone obrazy natywne. W tym przypadku należy uruchomić Mpgo.exe z tej samej listy scenariusza i zestawu i użyć `–RemoveNativeImages` parametru, aby usunąć te obrazy natywne.|
|`-RemoveNativeImages`|Czyści z uruchomienia gdzie `–LeaveNativeImages` została określona. Jeśli określisz `-RemoveNativeImages`, Mpgo.exe ignoruje wszelkie argumenty, z wyjątkiem `-64bit` i `–AssemblyList`i kończy działanie po usunięciu wszystkich zinstrumentowanych obrazów natywnych.|

## <a name="remarks"></a>Uwagi
 Możesz używać ich obu `–AssemblyList` i `- AssemblyListFile` wiele razy w wierszu polecenia.

 Jeśli nie określisz pełnych ścieżek podczas określania zestawów, Mpgo.exe będzie ich szukać w bieżącym katalogu. Jeśli określona ścieżka jest niepoprawna, Mpgo.exe wyświetla komunikat o błędzie, ale kontynuuje generowanie danych dla innych zestawów. Jeśli określisz zestaw, który nie jest ładowany podczas scenariusza szkoleniowego, żadne dane szkoleniowe nie są generowane dla tego zestawu.

 Jeśli zestaw na liście jest w globalnej pamięci podręcznej zestawów, nie będzie można zaktualizować go, aby zawierał informacje o profilu.  Usuń go z globalnej pamięci podręcznej zestawów, aby zebrać informacje o profilu.

 Użycie Ngen.exe i Mpgo.exe jest zalecane tylko dla dużych zarządzanych aplikacji, ponieważ korzyści wynikające ze wstępnie skompilowanym obrazów natywnych zazwyczaj są widoczne tylko wtedy, gdy eliminuje dużą część kompilacji JIT w czasie wykonywania. Uruchamianie Mpgo.exe w aplikacjach stylu "Hello World", które nie są dużymi zestawami nie daje żadnych korzyści, a Mpgo.exe może nawet ulec awarii podczas zbierania danych profilu.

> [!NOTE]
> Nie zaleca się stosowania Ngen.exe i Mpgo.exe w odniesieniu do aplikacji ASP.NET i usług Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Aby użyć Mpgo.exe  
  
1.  Użyj komputera, na którym zainstalowano Visual Studio Ultimate 2012 i aplikację.  
  
2.  Uruchom Mpgo.exe jako administrator z wymaganymi parametrami.  W następnej sekcji znajdują się przykładowe polecenia.  
  
     Zestawy zoptymalizowane języka pośredniego (IL) są tworzone w folderze określonym przez `–OutDir` parametru (przykłady to `C:\Optimized` folder).  
  
3.  Zamień zestawy IL używane dla Ngen.exe z nowymi zestawami IL, które zawierają informacje o profilu z katalogu określonego przez `–OutDir`.  
  
4.  Instalator aplikacji (przy użyciu obrazów dostarczonych przez Mpgo.exe) zainstaluje zoptymalizowane obrazy natywne.  
  
## <a name="suggested-workflow"></a>Sugerowany przebieg pracy  
  
1.  Utwórz zestaw zoptymalizowanych zestawów IL przy użyciu Mpgo.exe z `–Scenario` parametru.  
  
2.  Sprawdź zoptymalizowane zestawy IL w kontroli źródła.  
  
3.  W procesie kompilacji Wywołaj Mpgo.exe z `–Import` parametru jako krok po kompilacji w celu wygenerowania zoptymalizowanych obrazów IL do przekazania do Ngen.exe.  
  
 Ten proces daje pewność, że wszystkie zestawy posiadają dane optymalizacji. Jeśli ewidencjonujesz zaktualizowane zoptymalizowane zestawy (kroki 1 i 2) częściej, wydajności będą spójniejsze w całym procesie tworzenia produktu.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Przy użyciu Mpgo.exe z Visual Studio  
 Mpgo.exe można uruchomić z programu Visual Studio (zapoznaj się z artykułem [jak: Specify Build Events (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) z następującymi zastrzeżeniami:  
  
-   Nie można używać ścieżek w cudzysłowie ze znakami ukośnika na końcu, ponieważ makra Visual Studio również domyślnie używają końcowych ukośników. (Na przykład `–OutDir "C:\Output Folder\"` jest nieprawidłowy.) Aby obejść to ograniczenie, można pominąć końcowy ukośnik. (Na przykład użyć `-OutDir "$(OutDir)\"` zamiast.)  
  
-   Domyślnie program Mpgo.exe nie znajduje się w ścieżce kompilacji programu Visual Studio. Możesz dodać ścieżkę do programu Visual Studio lub podać pełną ścieżkę w wierszu polecenia Mpgo. Można użyć dowolnego `–Scenario` lub `–Import` parametru w zdarzeniu po kompilacji w programie Visual Studio. Jednak typowy proces jest użycie `–Scenario` jeden raz z deweloperem polecenia wiersza dla programu Visual Studio, a następnie użyj `–Import` do zaktualizowania zoptymalizowanych zestawów po każdej kompilacji; na przykład: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Przykłady  
 Następujące polecenie Mpgo.exe z wiersz polecenia dla deweloperów programu Visual Studio optymalizuje aplikację podatkową:  
  
```  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Następujące polecenie Mpgo.exe optymalizuje zdrową aplikację:  
  
```  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Następujące polecenie Mpgo.exe korzysta z danych z zestawów wcześniej zoptymalizowanych do optymalizacji nowszych wersji zestawów:  
  
```  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Zobacz także
- [Ngen.exe (generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [Zwiększanie wydajności uruchamiania aplikacji klasycznych](https://go.microsoft.com/fwlink/p/?LinkId=248943)
- [Przegląd ulepszeń wydajności w .NET 4.5](https://go.microsoft.com/fwlink/p/?LinkId=249131)
