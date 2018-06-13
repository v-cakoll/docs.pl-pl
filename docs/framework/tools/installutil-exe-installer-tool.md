---
title: Installutil.exe (Narzędzie instalatora)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec7e498e0f0634d4f0e104247b430fb591f702ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410150"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Narzędzie instalatora)
Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach. To narzędzie działa w połączeniu z klasami <xref:System.Configuration.Install> przestrzeni nazw.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|`assembly`|Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora. Pominięcie tego parametru, jeśli chcesz określić przy użyciu silnej nazwy zestawu `/AssemblyName` opcji.|  
  
<a name="options"></a>   
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> —lub—<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/help` *Zestawu*<br /><br /> —lub—<br /><br /> `/?` *Zestawu*|Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe. Ta opcja dodaje tekst zwracany przez każdego składnika Instalator <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości InstallUtil.exe tekst pomocy.|  
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> , Culture =*ustawień regionalnych*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu. W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.<br /><br /> Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".|  
|`/InstallStateDir=[` *directoryName* `]`|Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu. Domyślnie, jest to katalog, w którym znajduje się zestaw.|  
|`/LogFile=`[*filename*]|Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji. Domyślnie jeśli `/LogFile` opcja zostanie pominięta, plik dziennika o nazwie *assemblyname*. InstallLog jest tworzony. Jeśli *filename* jest pominięty, plik dziennika nie jest generowany.|  
|`/LogToConsole`={`true`&#124;`false`}|Jeśli `true`, wyświetla dane wyjściowe do konsoli. Jeśli `false` (ustawienie domyślne), pomija dane wyjściowe do konsoli.|  
|`/ShowCallStack`|Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.|  
|`/u`[`ninstall`]|Odinstalowuje określone zestawy. W przeciwieństwie do innych opcji `/u` ma zastosowanie do wszystkich zestawów niezależnie od tego, gdzie jest dostępna w wierszu polecenia.|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a>Dodatkowe opcje instalatora  
 Indywidualne instalatory użyte w zestawie mogą rozpoznawać opcje Ponadto uprawnienia wymienione w [opcje](#options) sekcji. Aby dowiedzieć się więcej o tych opcjach, uruchom InstallUtil.exe ze ścieżkami zestawów w wierszu polecenia, wraz z `/?` lub `/help` opcji. Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.  
  
> [!NOTE]
>  Zwraca tekst pomocy na opcje obsługiwane przez Instalator poszczególne składniki <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości. Poszczególne opcje, które zostały wprowadzone w wierszu polecenia są dostępne programowo z <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> właściwości.  
  
 Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji. Jednak jeśli używasz `/Password` parametr, który jest rozpoznawany przez niektóre składniki Instalatora, zostanie zastąpiony przez osiem gwiazdki (*) informacji o hasłach i nie pojawią się w pliku dziennika.  
  
> [!IMPORTANT]
>  W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu. Aby temu zapobiec, można pominąć w pliku dziennika, określając `/LogFile=` (bez *filename* argument) po Installutil.exe w wierszu polecenia.  
  
## <a name="remarks"></a>Uwagi  
 Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji. Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji. Program Installutil.exe wykrywa i wykonuje te składniki instalatora.  
  
 W jednym wierszu polecenia można określić wiele zestawów. Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu. Z wyjątkiem `/u` i `/AssemblyName`, opcje są zbiorczą, ale możliwym do zastąpienia. Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.  
  
 Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:  
  
-   InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.  
  
-   *AssemblyName*. InstallLog — zawiera informacje specyficzne dla fazy rezerwacji procesu instalacji. Aby uzyskać więcej informacji dotyczących fazy rezerwacji, zobacz <xref:System.Configuration.Install.Installer.Commit%2A> metody.  
  
-   *AssemblyName*. InstallState - zawiera dane używane w celu odinstalowania zestawu.  
  
 Installutil.exe używa odbicia, aby sprawdzić określonych zestawów i Znajdź wszystkie <xref:System.Configuration.Install.Installer> typów, które mają <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> ustawić atrybutu `true`. Narzędzie wykonuje następnie jedną <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> lub <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metody na każde wystąpienie <xref:System.Configuration.Install.Installer> typu. Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów. Odinstalowanie nie jest transakcyjne.  
  
 Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.  
  
 Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator. Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL). Obie wersje narzędzia instalatora działają tak samo.  
  
 Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++. Jeśli spróbujesz takich jak wdrożyć usługę Windows w języku C++ z Installutil.exe, wyjątek <xref:System.BadImageFormatException> zostanie wygenerowany. Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.  
  
```  
installutil /?  
```  
  
 Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe. Wyświetla również opis oraz listę obsługiwanych przez składniki Instalatora w opcji `myAssembly.exe` Jeśli przypisano tekst pomocy do Instalatora <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości.  
  
```  
installutil /? myAssembly.exe  
```  
  
 Polecenie wykonuje składników Instalatora w zestawie `myAssembly.exe`.  
  
```  
installutil myAssembly.exe  
```  
  
 Polecenie wykonuje składników Instalatora w zestawie przy użyciu `/AssemblyName` przełącznika i w pełni kwalifikowanej nazwy.  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę. Uwaga, wszystkie zestawy określonego za pomocą nazwy pliku musi poprzedzać zestawy określone przez silnej nazwy w wierszu polecenia, ponieważ `/AssemblyName` opcji nie może zostać zastąpiona.  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Polecenie wykonuje składniki dezinstalatora w zestawie `myAssembly.exe`.  
  
```  
installutil /u myAssembly.exe   
```  
  
 Polecenie wykonuje składniki uninistaller zestawy `myAssembly1.exe` i `myAssembly2.exe`.  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 Ponieważ pozycja `/u` opcji w wierszu polecenia nie jest ważna, jest odpowiednikiem następującego polecenia.  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 Polecenie wykonuje instalatorów w zestawie `myAssembly.exe` i określa, czy informacje o postępie będą zapisywane `myLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 Polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, określa, czy mają być zapisywane informacje o postępie `myLog.InstallLog`i używa niestandardowych instalatorów `/reg` opcję, aby określić, że należy dokonać aktualizacji do systemu rejestr.  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 Polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, używa niestandardowego obiektu Instalator `/email` opcję, aby określić adres e-mail użytkownika, a pomija dane wyjściowe do pliku dziennika.  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 Poniższe polecenie zapisuje postęp instalacji dla `myAssembly.exe` do `myLog.InstallLog` i zapisuje postęp `myTestAssembly.exe` do `myTestLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.Install>  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
