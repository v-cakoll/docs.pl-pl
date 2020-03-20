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
ms.openlocfilehash: 0052475697dae2c3ad891db18d300b5ec08a7e62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180348"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)

Narzędzie do optymalizacji z przewodnikiem profilu zarządzanego (Mpgo.exe) jest narzędziem wiersza polecenia, które używa typowych scenariuszy dla użytkowników końcowych w celu optymalizacji natywnych zestawów obrazów utworzonych przez [natywny generator obrazów (Ngen.exe).](ngen-exe-native-image-generator.md) To narzędzie umożliwia uruchamianie scenariuszy szkoleniowych, które generują dane profilu. Generator [obrazów natywnych (Ngen.exe)](ngen-exe-native-image-generator.md) używa tych danych do optymalizacji jego wygenerowanych zestawów aplikacji obrazu macierzystego. Scenariusz szkoleniowy jest próbnym uruchomieniem oczekiwanego użycia aplikacji. Mpgo.exe jest dostępny w programie Visual Studio Ultimate 2012 i jego nowszych wersjach. Począwszy od programu Visual Studio 2013, można również użyć mpgo.exe do optymalizacji aplikacji ze Sklepu Windows 8.x.  
  
Profilowana optymalizacja poprawia czas uruchamiania aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepustowość przez zbieranie danych ze scenariuszy szkoleniowych i używanie ich do optymalizowania układu obrazów natywnych.  
  
Jeśli wystąpią problemy z wydajnością czasu uruchamiania i rozmiarem zestawu roboczego dla zestawów języka pośredniego (IL), zaleca się użyć w pierwszej kolejności Ngen.exe, aby wyeliminować koszty kompilacji JIT oraz umożliwić udostępnianie kodu. Jeśli potrzebujesz dodatkowych usprawnień, możesz użyć Mpgo.exe do dalszej optymalizacji aplikacji. Dane dotyczące wydajności z zestawów niezoptymalizowanego obrazu natywnego można zastosować jako podstawę do oszacowania wzrostu wydajności. Użycie Mpgo.exe może spowodować przyspieszenie zimnego uruchamiania i zmniejszenie rozmiaru zestawu roboczego. Mpgo.exe dodaje informacje do zestawów IL, których Ngen.exe używa do tworzenia zoptymalizowanych zestawów obrazu natywnego. Aby uzyskać więcej informacji, zobacz wpis [Poprawianie wydajności uruchamiania aplikacji klasycznych](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) w blogu .NET.  
  
To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7) z poświadczeniami administratora i wpisz następujące polecenie w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
W przypadku aplikacji klasycznych:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
W przypadku aplikacji ze Sklepu Windows 8.x:  
  
## <a name="syntax"></a>Składnia  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametry  
 We wszystkich argumentach programu Mpgo.exe nie jest rozróżniana wielkość liter. Polecenia są poprzedzone kreską.  
  
> [!NOTE]
> Można użyć albo `–Scenario` `–Import` lub jako wymagane polecenie, ale nie oba. Żaden z wymaganych parametrów nie `–Reset` jest używany, jeśli określisz opcję.

|Wymagany parametr|Opis|
|------------------------|-----------------|
|`-Scenario`\< *polecenie*><br /><br /> —lub—<br /><br /> `-Scenario`\< *nazwa pakietu*><br /><br /> — lub —<br /><br /> `-Import`\< *katalog*>|W przypadku aplikacji `–Scenario` klasycznych należy określić polecenie uruchamiania aplikacji, którą chcesz zoptymalizować, w tym wszystkie argumenty wiersza polecenia. Użyj trzech zestawów podwójnych cudzysłowów wokół *polecenia,* jeśli określa ścieżkę zawierającą spacje; na przykład: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Nie należy używać podwójnych cudzysłowów; nie będą działać poprawnie, jeśli *polecenie* zawiera spacje.<br /><br /> — lub —<br /><br /> W przypadku aplikacji ze Sklepu `–Scenario` Windows 8.x służy do określania pakietu, dla którego chcesz wygenerować informacje o profilu. Jeśli określisz nazwę wyświetlaną pakietu lub nazwę rodziny pakietów zamiast pełnej nazwy pakietu, Mpgo.exe wybierze pakiet, który pasuje do podanej nazwy, pod warunkiem, że istnieje tylko jedno dopasowanie. Jeśli kilka pakietów odpowiada określonej nazwie, Mpgo.exe wyświetli monit o wybrania pakietu.<br /><br /> —lub—<br /><br /> Służy `-Import` do określania, że dane optymalizacji z wcześniej zoptymalizowanych zestawów `-AssemblyList`powinny być używane do optymalizacji złożeń w . *katalog* określa katalog zawierający wcześniej zoptymalizowane pliki. Zestawy określone w `–AssemblyList` `–AssemblyListFile` lub są nowe wersje zestawów, które mają być zoptymalizowane przy użyciu danych z importowanych plików. Używanie danych optymalizacji ze starszych wersji zestawów pozwala zoptymalizować nowsze wersje zestawów bez ponownego uruchamiania scenariusza.  Jednakże, jeśli zaimportowany i docelowy zestaw zawierają znacznie różniący się kod, dane optymalizacji będą nieskuteczne. Nazwy zestawów `–AssemblyList` określone `–AssemblyListFile` w katalogu określonym lub `–Import`muszą być obecne w katalogu określonym przez *katalog*. Użyj trzech zestawów podwójnych cudzysłowów wokół *katalogu,* jeśli określa ścieżkę zawierającą spacje.<br /><br /> Należy określić `–Scenario` oba `–Import`lub , ale nie oba parametry.|
|`-OutDir`\< *katalog*>|Katalog, w którym będą umieszczone zoptymalizowane zestawy. Jeśli zestaw już istnieje w folderze katalogu wyjściowego, tworzona jest nowa kopia i numer indeksu jest dołączany do jego nazwy; na przykład: *nazwa zestawu*-1.exe. Użyj podwójnych cudzysłowów wokół *katalogu,* jeśli określa ścieżkę zawierającą spacje.|
|`-AssemblyList`\< *assembly1 assembly2 ...*><br /><br /> —lub—<br /><br /> `-AssemblyListFile`\< *plik*>|Lista zestawów (w tym pliki exe i dll) rozdzielonych spacjami, dla których chcesz zbierać informacje profilowe. Można `C:\Dir\*.dll` określić `*.dll` lub wybrać wszystkie zestawy w wyznaczonym lub bieżącym katalogu roboczym. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.<br /><br /> —lub—<br /><br /> Plik tekstowy, który zawiera listę zestawów, dla których chcesz zebrać informacje o profilu. W każdym wierszu wymieniony jest jeden zestaw. Jeśli nazwa zestawu rozpoczyna się łącznikiem (-), użyj listy plików zestawów lub zmień nazwę zestawu.|
|`-AppID`\< *appId (ida)*>|Identyfikator aplikacji w określonym pakiecie. Jeśli użyjesz symbolu wieloznacznego (\*), Mpgo.exe spróbuje wyliczyć identyfikatory \<appid w pakiecie i powróci do *package_family_name*>! Aplikacja, jeśli się nie powiedzie. Jeżeli określono ciąg, który jest poprzedzony znakiem wykrzyknika (!), Mpgo.exe będzie łączyć nazwę rodziny pakietu z dostarczonym argumentem.|
|`-Timeout`\< *sekundy*>|Czas umożliwiający uruchamianie aplikacji ze Sklepu Windows 8.x przed zamknięciem aplikacji.|

|Parametr opcjonalny|Opis|
|------------------------|-----------------|
|`-64bit`|Instrumentuje zestawy do systemów 64-bitowych.  Nawet jeśli zestaw jest zadeklarowany jako 64-bitowy, należy określić ten parametr dla zestawów 64-bitowych.|
|`-ExeConfig`\< *nazwa pliku*>|Określa plik konfiguracji używany przez scenariusz do określenia informacje o wersji i module ładującym.|
|`-f`|Wymusza umieszczenie danych profilu w zestawie binarnym, nawet jeśli jest podpisany.  Jeśli zestaw jest podpisany, musi zostać ponownie podpisany; w przeciwnym razie zestawu nie będzie można załadować i uruchomić.|
|`-Reset`|Resetuje środowisko, aby była pewność, że przerwane sesje profilowania nie mają wpływu na swoje zestawy, a następnie kończy działanie. Środowisko jest resetowane domyślnie przed i po sesji profilowania.|
|`-Timeout`\< *czas w sekundach*>|Określa czas profilowania w sekundach. Użyj wartości, która jest nieco większa niż obserwowane czasy uruchamiania aplikacji GUI. Na koniec limitu czasu dane profilu są rejestrowana, mimo że aplikacja kontynuuje działanie. Jeśli ta opcja nie zostanie ustawiona, profilowanie będzie kontynuowane do czasu zamknięcia aplikacji, w czasie którym dane będą rejestrowane.|
|`-LeaveNativeImages`|Określa, że zinstrumentowane obrazy natywne nie powinny zostać usunięte po uruchomieniu tego scenariusza. Ta opcja jest używana przede wszystkim, gdy uzyskujesz aplikację, którą określono dla działającego scenariusza. Uniemożliwi to odtworzenie obrazów natywnych dla kolejnych uruchomień Mpgo.exe. W przypadku użycia tej opcji opcję w pamięci podręcznej po zakończeniu działania aplikacji mogą znajdować się oddzielone obrazy natywne. W takim przypadku uruchom plik Mpgo.exe z tą `–RemoveNativeImages` samą listą scenariuszy i zestawów oraz użyj parametru, aby usunąć te obrazy natywne.|
|`-RemoveNativeImages`|Czyści z przebiegu, gdzie `–LeaveNativeImages` został określony. Jeśli określisz `-RemoveNativeImages`, Mpgo.exe ignoruje wszelkie argumenty z wyjątkiem `-64bit` i `–AssemblyList`, i kończy się po usunięciu wszystkich instrumentowanych obrazów natywnych.|

## <a name="remarks"></a>Uwagi
 W wierszu `–AssemblyList` `- AssemblyListFile` polecenia można używać zarówno i wiele razy.

 Jeśli nie określisz pełnych ścieżek podczas określania zestawów, Mpgo.exe będzie ich szukać w bieżącym katalogu. Jeśli określona ścieżka jest niepoprawna, Mpgo.exe wyświetla komunikat o błędzie, ale kontynuuje generowanie danych dla innych zestawów. Jeśli określisz zestaw, który nie jest ładowany podczas scenariusza szkoleniowego, żadne dane szkoleniowe nie są generowane dla tego zestawu.

 Jeśli zestaw na liście jest w globalnej pamięci podręcznej zestawów, nie będzie można zaktualizować go, aby zawierał informacje o profilu.  Usuń go z globalnej pamięci podręcznej zestawów, aby zebrać informacje o profilu.

 Użycie Ngen.exe i Mpgo.exe jest zalecane tylko dla dużych zarządzanych aplikacji, ponieważ korzyści wynikające ze wstępnie skompilowanym obrazów natywnych zazwyczaj są widoczne tylko wtedy, gdy eliminuje dużą część kompilacji JIT w czasie wykonywania. Uruchamianie mpgo.exe w aplikacjach w stylu "Hello World", które nie są intensywne, nie zapewni żadnych korzyści, a mpgo.exe może nawet nie zebrać danych profilu.

> [!NOTE]
> Nie zaleca się stosowania Ngen.exe i Mpgo.exe w odniesieniu do aplikacji ASP.NET i usług Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Aby użyć Mpgo.exe  
  
1. Użyj komputera, na którym zainstalowano Visual Studio Ultimate 2012 i aplikację.  
  
2. Uruchom Mpgo.exe jako administrator z wymaganymi parametrami.  W następnej sekcji znajdują się przykładowe polecenia.  
  
     Zoptymalizowane zestawy języka pośredniego (IL) są tworzone `–OutDir` w folderze określonym przez parametr `C:\Optimized` (w przykładach jest to folder).  
  
3. Zastąp zestawy IL używane dla Ngen.exe nowymi zestawami IL, które zawierają `–OutDir`informacje o profilu z katalogu określonego przez program .  
  
4. Instalator aplikacji (przy użyciu obrazów dostarczonych przez Mpgo.exe) zainstaluje zoptymalizowane obrazy natywne.  
  
## <a name="suggested-workflow"></a>Sugerowany przebieg pracy  
  
1. Utwórz zestaw zoptymalizowanych zestawów IL przy użyciu mpgo.exe z parametrem. `–Scenario`  
  
2. Sprawdź zoptymalizowane zestawy IL w kontroli źródła.  
  
3. W procesie kompilacji wywołaj plik Mpgo.exe z `–Import` parametrem jako krok po kompilacji, aby wygenerować zoptymalizowane obrazy IL, aby przejść do pliku Ngen.exe.  
  
 Ten proces daje pewność, że wszystkie zestawy posiadają dane optymalizacji. Jeśli ewidencjonujesz zaktualizowane zoptymalizowane zestawy (kroki 1 i 2) częściej, wydajności będą spójniejsze w całym procesie tworzenia produktu.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Przy użyciu Mpgo.exe z Visual Studio  
 Program Mpgo.exe można uruchomić w programie Visual Studio (zobacz artykuł [Jak: Określanie zdarzeń kompilacji (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)z następującymi ograniczeniami:  
  
- Nie można używać ścieżek w cudzysłowie ze znakami ukośnika na końcu, ponieważ makra Visual Studio również domyślnie używają końcowych ukośników. (Na przykład `–OutDir "C:\Output Folder\"` jest nieprawidłowy.) Aby obejść to ograniczenie, można uniknąć końcowego ukośnika. (Na przykład `-OutDir "$(OutDir)\"` użyj zamiast tego).  
  
- Domyślnie program Mpgo.exe nie znajduje się w ścieżce kompilacji programu Visual Studio. Możesz dodać ścieżkę do programu Visual Studio lub podać pełną ścieżkę w wierszu polecenia Mpgo. Można użyć `–Scenario` lub parametru `–Import` w zdarzeniu po kompilacji w programie Visual Studio. Jednak typowy proces jest `–Scenario` użycie jeden raz z wiersza polecenia dewelopera dla programu Visual Studio, a następnie użyć `–Import` do aktualizacji zoptymalizowanych zestawów po każdej kompilacji; na przykład: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>
## <a name="examples"></a>Przykłady  
 Następujące polecenie Mpgo.exe z wiersza polecenia dewelopera dla programu Visual Studio optymalizuje aplikację podatkową:  
  
```console  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Następujące polecenie Mpgo.exe optymalizuje zdrową aplikację:  
  
```console  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Następujące polecenie Mpgo.exe korzysta z danych z zestawów wcześniej zoptymalizowanych do optymalizacji nowszych wersji zestawów:  
  
```console  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Zobacz też

- [Ngen.exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
- [Poprawa wydajności uruchamiania aplikacji komputerowych](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [Omówienie poprawy wydajności w programie .NET 4.5](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
