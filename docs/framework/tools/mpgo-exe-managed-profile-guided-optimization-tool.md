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
ms.openlocfilehash: a5ab3040a246a135771c45b2639567db9ab510e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447970"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)

The Managed Profile Guided Optimization Tool (Mpgo.exe) is a command-line tool that uses common end-user scenarios to optimize the native image assemblies that are created by the [Native Image Generator (Ngen.exe)](ngen-exe-native-image-generator.md). To narzędzie umożliwia uruchamianie scenariuszy szkoleniowych, które generują dane profilu. The [Native Image Generator (Ngen.exe)](ngen-exe-native-image-generator.md) uses this data to optimize its generated native image application assemblies. Scenariusz szkoleniowy jest próbnym uruchomieniem oczekiwanego użycia aplikacji. Mpgo.exe jest dostępny w programie Visual Studio Ultimate 2012 i jego nowszych wersjach. Starting with Visual Studio 2013, you can also use Mpgo.exe to optimize Windows 8.x Store apps.  
  
Profilowana optymalizacja poprawia czas uruchamiania aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepustowość przez zbieranie danych ze scenariuszy szkoleniowych i używanie ich do optymalizowania układu obrazów natywnych.  
  
Jeśli wystąpią problemy z wydajnością czasu uruchamiania i rozmiarem zestawu roboczego dla zestawów języka pośredniego (IL), zaleca się użyć w pierwszej kolejności Ngen.exe, aby wyeliminować koszty kompilacji JIT oraz umożliwić udostępnianie kodu. Jeśli potrzebujesz dodatkowych usprawnień, możesz użyć Mpgo.exe do dalszej optymalizacji aplikacji. Dane dotyczące wydajności z zestawów niezoptymalizowanego obrazu natywnego można zastosować jako podstawę do oszacowania wzrostu wydajności. Użycie Mpgo.exe może spowodować przyspieszenie zimnego uruchamiania i zmniejszenie rozmiaru zestawu roboczego. Mpgo.exe dodaje informacje do zestawów IL, których Ngen.exe używa do tworzenia zoptymalizowanych zestawów obrazu natywnego. For more information, see the entry [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) in the .NET blog.  
  
To narzędzie jest instalowane automatycznie z programem Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials, and type the following at the command prompt. For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
W przypadku aplikacji klasycznych:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
For Windows 8.x Store apps:  
  
## <a name="syntax"></a>Składnia  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametry  
 We wszystkich argumentach programu Mpgo.exe nie jest rozróżniana wielkość liter. Polecenia są poprzedzone kreską.  
  
> [!NOTE]
> You can use either `–Scenario` or `–Import` as a required command, but not both. None of the required parameters are used if you specify the `–Reset` option.

|Wymagany parametr|Opis|
|------------------------|-----------------|
|`-Scenario` \<*command*><br /><br /> —lub—<br /><br /> `-Scenario` \<*packageName*><br /><br /> —lub—<br /><br /> `-Import` \<*directory*>|For desktop apps, use `–Scenario` to specify the command to run the application you want to optimize, including any command-line arguments. Use three sets of double quotation marks around *command* if it specifies a path that includes spaces; for example: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Do not use double quotation marks; they will not work correctly if *command* includes spaces.<br /><br /> —lub—<br /><br /> For Windows 8.x Store apps, use `–Scenario` to specify the package that you want to generate profile information for. Jeśli określisz nazwę wyświetlaną pakietu lub nazwę rodziny pakietów zamiast pełnej nazwy pakietu, Mpgo.exe wybierze pakiet, który pasuje do podanej nazwy, pod warunkiem, że istnieje tylko jedno dopasowanie. Jeśli kilka pakietów odpowiada określonej nazwie, Mpgo.exe wyświetli monit o wybrania pakietu.<br /><br /> —lub—<br /><br /> Use `-Import` to specify that optimization data from previously optimized assemblies should be used to optimize the assemblies in `-AssemblyList`. *directory* specifies the directory that contains the previously optimized files. The assemblies specified in `–AssemblyList` or `–AssemblyListFile` are the new versions of the assemblies to be optimized using the data from the imported files. Używanie danych optymalizacji ze starszych wersji zestawów pozwala zoptymalizować nowsze wersje zestawów bez ponownego uruchamiania scenariusza.  Jednakże, jeśli zaimportowany i docelowy zestaw zawierają znacznie różniący się kod, dane optymalizacji będą nieskuteczne. The assembly names specified in `–AssemblyList` or `–AssemblyListFile` must be present in the directory specified by `–Import`*directory*. Use three sets of double quotation marks around *directory* if it specifies a path that includes spaces.<br /><br /> You must specify either `–Scenario` or `–Import`, but not both parameters.|
|`-OutDir` \<*directory*>|Katalog, w którym będą umieszczone zoptymalizowane zestawy. If an assembly already exists in the output directory folder, a new copy is created and an index number is appended to its name; for example: *assemblyname*-1.exe. Use double quotation marks around *directory* if it specifies a path that contains spaces.|
|`-AssemblyList` \<*assembly1 assembly2 ...* ><br /><br /> —lub—<br /><br /> `-AssemblyListFile` \<*file*>|Lista zestawów (w tym pliki exe i dll) rozdzielonych spacjami, dla których chcesz zbierać informacje profilowe. You can specify `C:\Dir\*.dll` or `*.dll` to select all the assemblies in the designated or current working directory. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.<br /><br /> —lub—<br /><br /> Plik tekstowy, który zawiera listę zestawów, dla których chcesz zebrać informacje o profilu. W każdym wierszu wymieniony jest jeden zestaw. Jeśli nazwa zestawu rozpoczyna się łącznikiem (-), użyj listy plików zestawów lub zmień nazwę zestawu.|
|`-AppID` \<*appId*>|Identyfikator aplikacji w określonym pakiecie. If you use the wildcard (\*), Mpgo.exe will try to enumerate the AppIDs in the package and will fall back to \<*package_family_name*>!App if it fails. Jeżeli określono ciąg, który jest poprzedzony znakiem wykrzyknika (!), Mpgo.exe będzie łączyć nazwę rodziny pakietu z dostarczonym argumentem.|
|`-Timeout` \<*seconds*>|The amount of time to allow the Windows 8.x Store app to run before the app exits.|

|Parametr opcjonalny|Opis|
|------------------------|-----------------|
|`-64bit`|Instrumentuje zestawy do systemów 64-bitowych.  Nawet jeśli zestaw jest zadeklarowany jako 64-bitowy, należy określić ten parametr dla zestawów 64-bitowych.|
|`-ExeConfig` \<*filename*>|Określa plik konfiguracji używany przez scenariusz do określenia informacje o wersji i module ładującym.|
|`-f`|Wymusza umieszczenie danych profilu w zestawie binarnym, nawet jeśli jest podpisany.  Jeśli zestaw jest podpisany, musi zostać ponownie podpisany; w przeciwnym razie zestawu nie będzie można załadować i uruchomić.|
|`-Reset`|Resetuje środowisko, aby była pewność, że przerwane sesje profilowania nie mają wpływu na swoje zestawy, a następnie kończy działanie. Środowisko jest resetowane domyślnie przed i po sesji profilowania.|
|`-Timeout` \<*time in seconds*>|Określa czas profilowania w sekundach. Użyj wartości, która jest nieco większa niż obserwowane czasy uruchamiania aplikacji GUI. Na koniec limitu czasu dane profilu są rejestrowana, mimo że aplikacja kontynuuje działanie. Jeśli ta opcja nie zostanie ustawiona, profilowanie będzie kontynuowane do czasu zamknięcia aplikacji, w czasie którym dane będą rejestrowane.|
|`-LeaveNativeImages`|Określa, że zinstrumentowane obrazy natywne nie powinny zostać usunięte po uruchomieniu tego scenariusza. Ta opcja jest używana przede wszystkim, gdy uzyskujesz aplikację, którą określono dla działającego scenariusza. Uniemożliwi to odtworzenie obrazów natywnych dla kolejnych uruchomień Mpgo.exe. W przypadku użycia tej opcji opcję w pamięci podręcznej po zakończeniu działania aplikacji mogą znajdować się oddzielone obrazy natywne. In this case, run Mpgo.exe with the same scenario and assembly list and use the `–RemoveNativeImages` parameter to remove these native images.|
|`-RemoveNativeImages`|Cleans up from a run where `–LeaveNativeImages` was specified. If you specify `-RemoveNativeImages`, Mpgo.exe ignores any arguments except `-64bit` and `–AssemblyList`, and exits after removing all instrumented native images.|

## <a name="remarks"></a>Uwagi
 You can use both `–AssemblyList` and `- AssemblyListFile` multiple times on the command line.

 Jeśli nie określisz pełnych ścieżek podczas określania zestawów, Mpgo.exe będzie ich szukać w bieżącym katalogu. Jeśli określona ścieżka jest niepoprawna, Mpgo.exe wyświetla komunikat o błędzie, ale kontynuuje generowanie danych dla innych zestawów. Jeśli określisz zestaw, który nie jest ładowany podczas scenariusza szkoleniowego, żadne dane szkoleniowe nie są generowane dla tego zestawu.

 Jeśli zestaw na liście jest w globalnej pamięci podręcznej zestawów, nie będzie można zaktualizować go, aby zawierał informacje o profilu.  Usuń go z globalnej pamięci podręcznej zestawów, aby zebrać informacje o profilu.

 Użycie Ngen.exe i Mpgo.exe jest zalecane tylko dla dużych zarządzanych aplikacji, ponieważ korzyści wynikające ze wstępnie skompilowanym obrazów natywnych zazwyczaj są widoczne tylko wtedy, gdy eliminuje dużą część kompilacji JIT w czasie wykonywania. Running Mpgo.exe on "Hello World" style applications that aren’t working-set intensive will not provide any benefits, and Mpgo.exe may even fail to gather profile data.

> [!NOTE]
> Nie zaleca się stosowania Ngen.exe i Mpgo.exe w odniesieniu do aplikacji ASP.NET i usług Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Aby użyć Mpgo.exe  
  
1. Użyj komputera, na którym zainstalowano Visual Studio Ultimate 2012 i aplikację.  
  
2. Uruchom Mpgo.exe jako administrator z wymaganymi parametrami.  W następnej sekcji znajdują się przykładowe polecenia.  
  
     The optimized intermediate language (IL) assemblies are created in the folder specified by the `–OutDir` parameter (in the examples, this is the `C:\Optimized` folder).  
  
3. Replace the IL assemblies you used for Ngen.exe  with the new IL assemblies that contain the profile information from the directory specified by `–OutDir`.  
  
4. Instalator aplikacji (przy użyciu obrazów dostarczonych przez Mpgo.exe) zainstaluje zoptymalizowane obrazy natywne.  
  
## <a name="suggested-workflow"></a>Sugerowany przebieg pracy  
  
1. Create a set of optimized IL assemblies by using Mpgo.exe with the `–Scenario` parameter.  
  
2. Sprawdź zoptymalizowane zestawy IL w kontroli źródła.  
  
3. In the build process, call Mpgo.exe with the `–Import` parameter as a post-build step to generate optimized IL images to pass to Ngen.exe.  
  
 Ten proces daje pewność, że wszystkie zestawy posiadają dane optymalizacji. Jeśli ewidencjonujesz zaktualizowane zoptymalizowane zestawy (kroki 1 i 2) częściej, wydajności będą spójniejsze w całym procesie tworzenia produktu.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Przy użyciu Mpgo.exe z Visual Studio  
 You can run Mpgo.exe from Visual Studio (see the article [How to: Specify Build Events (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) with the following restrictions:  
  
- Nie można używać ścieżek w cudzysłowie ze znakami ukośnika na końcu, ponieważ makra Visual Studio również domyślnie używają końcowych ukośników. (For example, `–OutDir "C:\Output Folder\"` is invalid.) To work around this restriction, you can escape the trailing slash. (For example, use `-OutDir "$(OutDir)\"` instead.)  
  
- Domyślnie program Mpgo.exe nie znajduje się w ścieżce kompilacji programu Visual Studio. Możesz dodać ścieżkę do programu Visual Studio lub podać pełną ścieżkę w wierszu polecenia Mpgo. You can use either the `–Scenario` or the `–Import` parameter in the post-build event in Visual Studio. However, the typical process is to use `–Scenario` one time from a Developer Command Prompt for Visual Studio, and then use `–Import` to update the optimized assemblies after each build; for example:  `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Przykłady  
 The following Mpgo.exe command from a Developer Command Prompt for Visual Studio optimizes a tax application:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Ngen.exe (generator obrazu natywnego)](ngen-exe-native-image-generator.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
- [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [An Overview of Performance Improvements in .NET 4.5](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
