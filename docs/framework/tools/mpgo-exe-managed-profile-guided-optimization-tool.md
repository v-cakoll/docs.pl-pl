---
title: "Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b6c95613cdc7ac656e8beafcf9a685e51eddf5a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)
Zarządzane profil z przewodnikiem narzędzie optymalizacji (Mpgo.exe) jest narzędziem wiersza polecenia, korzystającą z typowych scenariuszy użytkownika końcowego w celu zoptymalizowania zestawy obrazu macierzystego, które zostały utworzone przy użyciu [Generator obrazu natywnego (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). To narzędzie umożliwia uruchamianie scenariuszy szkoleniowych, które generują dane profilu. [Generator obrazu natywnego (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) używa tych danych w celu optymalizowania jego zestawów aplikacji generowanego obrazu macierzystego. Scenariusz szkoleniowy jest próbnym uruchomieniem oczekiwanego użycia aplikacji. Mpgo.exe jest dostępny w programie Visual Studio Ultimate 2012 i jego nowszych wersjach. Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], umożliwia także Mpgo.exe w celu zoptymalizowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Profilowana optymalizacja poprawia czas uruchamiania aplikacji, wykorzystanie pamięci (rozmiar zestawu roboczego) i przepustowość przez zbieranie danych ze scenariuszy szkoleniowych i używanie ich do optymalizowania układu obrazów natywnych.  
  
 Jeśli wystąpią problemy z wydajnością czasu uruchamiania i rozmiarem zestawu roboczego dla zestawów języka pośredniego (IL), zaleca się użyć w pierwszej kolejności Ngen.exe, aby wyeliminować koszty kompilacji JIT oraz umożliwić udostępnianie kodu. Jeśli potrzebujesz dodatkowych usprawnień, możesz użyć Mpgo.exe do dalszej optymalizacji aplikacji. Dane dotyczące wydajności z zestawów niezoptymalizowanego obrazu natywnego można zastosować jako podstawę do oszacowania wzrostu wydajności. Użycie Mpgo.exe może spowodować przyspieszenie zimnego uruchamiania i zmniejszenie rozmiaru zestawu roboczego. Mpgo.exe dodaje informacje do zestawów IL, których Ngen.exe używa do tworzenia zoptymalizowanych zestawów obrazu natywnego. Aby uzyskać więcej informacji, zobacz wpis [poprawy wydajności uruchamiania aplikacji pulpit](http://go.microsoft.com/fwlink/p/?LinkId=248943) w blogu .NET.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7) z poświadczeniami administratora i wpisać następujące polecenie. Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W przypadku aplikacji klasycznych:  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
 Dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji:  
  
## <a name="syntax"></a>Składnia  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
#### <a name="parameters"></a>Parametry  
 We wszystkich argumentach programu Mpgo.exe nie jest rozróżniana wielkość liter. Polecenia są poprzedzone kreską.  
  
> [!NOTE]
>  Możesz użyć dowolnej `–Scenario` lub `–Import` jako wymagane polecenia, ale nie oba. Brak wymaganego parametru są używane, jeśli określono `–Reset` opcji.  
  
|Wymagany parametr|Opis|  
|------------------------|-----------------|  
|`-Scenario`\< *polecenia*><br /><br /> —lub—<br /><br /> `-Scenario`\< *packageName*><br /><br /> —lub—<br /><br /> `-Import`\< *katalogu*>|Dla aplikacji klasycznych, użyj `–Scenario` Aby określić polecenie do uruchomienia aplikacji chcesz zoptymalizować, włączając żadnych argumentów wiersza polecenia. Korzystanie z zestawów trzy znaki podwójnego cudzysłowu wokół *polecenia* Jeśli Określa ścieżkę, która zawiera spację; na przykład: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Nie należy używać podwójnych cudzysłowów prostych; będą one nie działać poprawnie Jeśli *polecenia* zawiera spacje.<br /><br /> —lub—<br /><br /> Aby uzyskać [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, użyj `–Scenario` do określ pakiet, który chcesz wygenerować informacje o profilu. Jeśli określisz nazwę wyświetlaną pakietu lub nazwę rodziny pakietów zamiast pełnej nazwy pakietu, Mpgo.exe wybierze pakiet, który pasuje do podanej nazwy, pod warunkiem, że istnieje tylko jedno dopasowanie. Jeśli kilka pakietów odpowiada określonej nazwie, Mpgo.exe wyświetli monit o wybrania pakietu.<br /><br /> —lub—<br /><br /> Użyj `-Import` do określenia tej optymalizacji dane z wcześniej zoptymalizowane zestawy mają służyć do optymalizacji zestawów w `-AssemblyList`. *katalog* Określa katalog, który zawiera wcześniej zoptymalizowanych plików. Zestawy określone `–AssemblyList` lub `–AssemblyListFile` są nowe wersje zestawy Optymalizacja przy użyciu danych z importowanych plików. Używanie danych optymalizacji ze starszych wersji zestawów pozwala zoptymalizować nowsze wersje zestawów bez ponownego uruchamiania scenariusza.  Jednakże, jeśli zaimportowany i docelowy zestaw zawierają znacznie różniący się kod, dane optymalizacji będą nieskuteczne. Nazwy zestawu określonego w `–AssemblyList` lub `–AssemblyListFile` musi znajdować się w katalogu określonym przez `–Import` *katalogu*. Korzystanie z zestawów trzy znaki podwójnego cudzysłowu wokół *katalogu* Jeśli Określa ścieżkę, która zawiera spacje.<br /><br /> Należy określić `–Scenario` lub `–Import`, ale nie oba parametry.|  
|`-OutDir`\< *katalogu*>|Katalog, w którym będą umieszczone zoptymalizowane zestawy. Jeśli zestaw został już istnieje w folderze wyjściowym katalogu, utworzono nową kopię i numer indeksu jest dołączany do nazwy; na przykład: *assemblyname*-1.exe. Użyj podwójnego cudzysłowu *katalogu* jeśli określa ścieżki, która zawiera spacje.|  
|`-AssemblyList`\< *assembly2 zestaw1...*><br /><br /> —lub—<br /><br /> `-AssemblyListFile`\< *pliku*>|Lista zestawów (w tym pliki exe i dll) rozdzielonych spacjami, dla których chcesz zbierać informacje profilowe. Można określić `C:\Dir\*.dll` lub `*.dll` zaznacz wszystkie zestawy w wyznaczonym lub bieżący katalog roboczy. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.<br /><br /> —lub—<br /><br /> Plik tekstowy, który zawiera listę zestawów, dla których chcesz zebrać informacje o profilu. W każdym wierszu wymieniony jest jeden zestaw. Jeśli nazwa zestawu rozpoczyna się łącznikiem (-), użyj listy plików zestawów lub zmień nazwę zestawu.|  
|`-AppID`\< *appId*>|Identyfikator aplikacji w określonym pakiecie. Jeśli używasz symbolu wieloznacznego (\*), Mpgo.exe będzie próbował wyliczyć AppIDs w pakiecie i powróci \< *package_family_name*>! Aplikacja, jeśli działanie nie powiodło się. Jeżeli określono ciąg, który jest poprzedzony znakiem wykrzyknika (!), Mpgo.exe będzie łączyć nazwę rodziny pakietu z dostarczonym argumentem.|  
|`-Timeout`\< *sekund*>|Ilość czasu, aby umożliwić [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji do uruchomienia przed umożliwia zamknięcie aplikacji.|  
  
|Parametr opcjonalny|Opis|  
|------------------------|-----------------|  
|`-64bit`|Instrumentuje zestawy do systemów 64-bitowych.  Nawet jeśli zestaw jest zadeklarowany jako 64-bitowy, należy określić ten parametr dla zestawów 64-bitowych.|  
|`-ExeConfig`\< *filename*>|Określa plik konfiguracji używany przez scenariusz do określenia informacje o wersji i module ładującym.|  
|`-f`|Wymusza umieszczenie danych profilu w zestawie binarnym, nawet jeśli jest podpisany.  Jeśli zestaw jest podpisany, musi zostać ponownie podpisany; w przeciwnym razie zestawu nie będzie można załadować i uruchomić.|  
|`-Reset`|Resetuje środowisko, aby była pewność, że przerwane sesje profilowania nie mają wpływu na swoje zestawy, a następnie kończy działanie. Środowisko jest resetowane domyślnie przed i po sesji profilowania.|  
|`-Timeout`\< *czas w sekundach*>|Określa czas profilowania w sekundach. Użyj wartości, która jest nieco większa niż obserwowane czasy uruchamiania aplikacji GUI. Na koniec limitu czasu dane profilu są rejestrowana, mimo że aplikacja kontynuuje działanie. Jeśli ta opcja nie zostanie ustawiona, profilowanie będzie kontynuowane do czasu zamknięcia aplikacji, w czasie którym dane będą rejestrowane.|  
|`-LeaveNativeImages`|Określa, że zinstrumentowane obrazy natywne nie powinny zostać usunięte po uruchomieniu tego scenariusza. Ta opcja jest używana przede wszystkim, gdy uzyskujesz aplikację, którą określono dla działającego scenariusza. Uniemożliwi to odtworzenie obrazów natywnych dla kolejnych uruchomień Mpgo.exe. W przypadku użycia tej opcji opcję w pamięci podręcznej po zakończeniu działania aplikacji mogą znajdować się oddzielone obrazy natywne. W takim przypadku należy uruchomić Mpgo.exe z tej samej listy scenariusza i zestawu i użyć `–RemoveNativeImages` parametr, aby usunąć te obrazów macierzystych.|  
|`-RemoveNativeImages`|Czyści z działania gdzie `–LeaveNativeImages` została określona. Jeśli określisz `-RemoveNativeImages`, Mpgo.exe ignoruje żadnych argumentów z wyjątkiem `-64bit` i `–AssemblyList`i zamyka po usunięciu wszystkich instrumentowanych obrazów macierzystych.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć zarówno `–AssemblyList` i `- AssemblyListFile` wiele razy w wierszu polecenia.  
  
 Jeśli nie określisz pełnych ścieżek podczas określania zestawów, Mpgo.exe będzie ich szukać w bieżącym katalogu. Jeśli określona ścieżka jest niepoprawna, Mpgo.exe wyświetla komunikat o błędzie, ale kontynuuje generowanie danych dla innych zestawów. Jeśli określisz zestaw, który nie jest ładowany podczas scenariusza szkoleniowego, żadne dane szkoleniowe nie są generowane dla tego zestawu.  
  
 Jeśli zestaw na liście jest w globalnej pamięci podręcznej zestawów, nie będzie można zaktualizować go, aby zawierał informacje o profilu.  Usuń go z globalnej pamięci podręcznej zestawów, aby zebrać informacje o profilu.  
  
 Użycie Ngen.exe i Mpgo.exe jest zalecane tylko dla dużych zarządzanych aplikacji, ponieważ korzyści wynikające ze wstępnie skompilowanym obrazów natywnych zazwyczaj są widoczne tylko wtedy, gdy eliminuje dużą część kompilacji JIT w czasie wykonywania. Uruchomiona Mpgo.exe na "Hello World" aplikacji, które nie są intensywnie zestaw roboczy nie zapewnia żadnych korzyści i Mpgo.exe może nawet nie zebrania danych profilu.  
  
> [!NOTE]
>  Nie zaleca się stosowania Ngen.exe i Mpgo.exe w odniesieniu do aplikacji ASP.NET i usług Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Aby użyć Mpgo.exe  
  
1.  Użyj komputera, na którym zainstalowano Visual Studio Ultimate 2012 i aplikację.  
  
2.  Uruchom Mpgo.exe jako administrator z wymaganymi parametrami.  W następnej sekcji znajdują się przykładowe polecenia.  
  
     Zestawy zoptymalizowane języka pośrednim (IL) są tworzone w folderze określonym przez `–OutDir` parametru (w przykładach jest `C:\Optimized` folderu).  
  
3.  Zastąp zestawy IL używane dla Ngen.exe z nowego zestawy IL, które zawierają informacje o profilu z katalogu określonego przez `–OutDir`.  
  
4.  Instalator aplikacji (przy użyciu obrazów dostarczonych przez Mpgo.exe) zainstaluje zoptymalizowane obrazy natywne.  
  
## <a name="suggested-workflow"></a>Sugerowany przebieg pracy  
  
1.  Tworzenie zestawu zestawów IL zoptymalizowane przy użyciu Mpgo.exe z `–Scenario` parametru.  
  
2.  Sprawdź zoptymalizowane zestawy IL w kontroli źródła.  
  
3.  W procesie kompilacji wywołać Mpgo.exe z `–Import` parametru krokiem po kompilacji do generowania zoptymalizowanych obrazów IL do przekazania do Ngen.exe.  
  
 Ten proces daje pewność, że wszystkie zestawy posiadają dane optymalizacji. Jeśli ewidencjonujesz zaktualizowane zoptymalizowane zestawy (kroki 1 i 2) częściej, wydajności będą spójniejsze w całym procesie tworzenia produktu.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Przy użyciu Mpgo.exe z Visual Studio  
 Mpgo.exe można uruchomić z programu Visual Studio (zapoznaj się z artykułem [porady: Określanie zdarzeń kompilacji (C#)](http://msdn.microsoft.com/library/b4ce1ad9-5215-4b6f-b6a2-798b249aa335)) z następującymi ograniczeniami:  
  
-   Nie można używać ścieżek w cudzysłowie ze znakami ukośnika na końcu, ponieważ makra Visual Studio również domyślnie używają końcowych ukośników. (Na przykład `–OutDir "C:\Output Folder\"` jest nieprawidłowy.) Aby obejść to ograniczenie, można pominąć końcowy ukośnik. (Na przykład użyć `-OutDir "$(OutDir)\"` zamiast.)  
  
-   Domyślnie program Mpgo.exe nie znajduje się w ścieżce kompilacji programu Visual Studio. Możesz dodać ścieżkę do programu Visual Studio lub podać pełną ścieżkę w wierszu polecenia Mpgo. Możesz użyć dowolnej `–Scenario` lub `–Import` parametru w zdarzenie mające miejsce po kompilacji w programie Visual Studio. Jednak typowy proces jest użycie `–Scenario` Monituj jeden raz z polecenia dla deweloperów programu Visual Studio, a następnie użyj `–Import` zaktualizować zoptymalizowane zestawy po każdej kompilacji; na przykład: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Przykłady  
 Następujące polecenie Mpgo.exe z deweloperskiego wiersza polecenia programu Visual Studio optymalizuje aplikację podatkową:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [Wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [Poprawianie wydajności uruchamianie aplikacji klasycznych](http://go.microsoft.com/fwlink/p/?LinkId=248943)  
 [Omówienie lepsza wydajność programu .NET 4.5](http://go.microsoft.com/fwlink/p/?LinkId=249131)
