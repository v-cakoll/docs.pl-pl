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
ms.openlocfilehash: caca946617c681ce6516b7184a9ea506cc67158d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105073"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Narzędzie instalatora)

Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach. To narzędzie działa w połączeniu z klasami w przestrzeni nazw <xref:System.Configuration.Install>.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Opis|
|--------------|-----------------|
|`assembly`|Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora. Pomiń ten parametr, jeśli chcesz określić silną nazwę zestawu przy użyciu opcji `/AssemblyName`.|

<a name="options"></a>

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/h[elp]`<br /><br /> —lub—<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|
|*zestaw* `/help`<br /><br /> —lub—<br /><br /> *zestaw* `/?`|Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe. Ta opcja powoduje dodanie tekstu zwróconego przez każdą właściwość <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> składnika Instalatora do tekstu pomocy programu InstallUtil. exe.|
|`/AssemblyName` "*AssemblyName*<br /><br /> , Version =*główna. pomocnicza. kompilacja. poprawka*<br /><br /> , Kultura =*Ustawienia regionalne*<br /><br /> , PublicKeyToken =*PublicKeyToken*"|Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu. W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.<br /><br /> Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".|
|`/InstallStateDir=[` *directoryname* `]`|Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu. Domyślnie, jest to katalog, w którym znajduje się zestaw.|
|`/LogFile=`[*filename*]|Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji. Domyślnie, jeśli opcja `/LogFile` zostanie pominięta, plik dziennika o nazwie *AssemblyName*. InstallLog. Jeśli *Nazwa pliku* zostanie pominięta, żaden plik dziennika nie zostanie wygenerowany.|
|`/LogToConsole`= {`true`&#124;`false`}|Jeśli `true`, wyświetla dane wyjściowe w konsoli programu. Jeśli `false` (wartość domyślna), pomija dane wyjściowe w konsoli programu.|
|`/ShowCallStack`|Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.|
|`/u`[`ninstall`]|Odinstalowuje określone zestawy. W przeciwieństwie do innych opcji, `/u` stosuje się do wszystkich zestawów niezależnie od tego, gdzie opcja pojawia się w wierszu polecenia.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Dodatkowe opcje instalatora

Poszczególne Instalatory używane w ramach zestawu mogą rozpoznawać opcje oprócz tych wymienionych w sekcji [Opcje](#options) . Aby dowiedzieć się więcej na temat tych opcji, uruchom program InstallUtil. exe z ścieżkami zestawów w wierszu polecenia wraz z opcją `/?` lub `/help`. Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.

> [!NOTE]
> Tekst pomocy na temat opcji obsługiwanych przez poszczególne składniki instalatora jest zwracany przez właściwość <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType>. Poszczególne opcje, które zostały wprowadzone w wierszu polecenia, są dostępne programowo z właściwości <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType>.

Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji. Jeśli jednak użyjesz parametru `/Password`, który jest rozpoznawany przez niektóre składniki instalatora, informacje o haśle zostaną zastąpione przez osiem gwiazdek (*) i nie będą wyświetlane w pliku dziennika.

> [!IMPORTANT]
> W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu. Aby uniknąć tego zachowania, można pominąć plik dziennika, określając `/LogFile=` (bez argumentu *filename* ) po Installutil. exe w wierszu polecenia.

## <a name="remarks"></a>Uwagi

Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji. Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji. Program Installutil.exe wykrywa i wykonuje te składniki instalatora.

W jednym wierszu polecenia można określić wiele zestawów. Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu. Z wyjątkiem `/u` i `/AssemblyName`, opcje są skumulowane, ale Zastąp. Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.

Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:

- InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.

- *AssemblyName*. InstallLog — zawiera informacje specyficzne dla fazy zatwierdzania procesu instalacji. Aby uzyskać więcej informacji na temat fazy zatwierdzania, zobacz metodę <xref:System.Configuration.Install.Installer.Commit%2A>.

- *AssemblyName*. InstallState — zawiera dane używane do odinstalowania zestawu.

Installutil. exe używa odbicia w celu sprawdzenia określonych zestawów i znalezienia wszystkich typów <xref:System.Configuration.Install.Installer>, które mają atrybut <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> ustawiony na `true`. Następnie narzędzie wykonuje <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> lub metodę <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> dla każdego wystąpienia typu <xref:System.Configuration.Install.Installer>. Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów. Odinstalowanie nie jest transakcyjne.

Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.

Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator. Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL). Obie wersje narzędzia instalatora działają tak samo.

Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++. Jeśli spróbujesz wdrożyć usługę C++ systemu Windows przy użyciu Installutil. exe, zostanie zgłoszony wyjątek, taki jak <xref:System.BadImageFormatException>. Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.

## <a name="examples"></a>Przykłady

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.

```console
installutil /?
```

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe. Wyświetla również opis i listę opcji obsługiwanych przez składniki instalatora w `myAssembly.exe`, jeśli tekst pomocy został przypisany do właściwości <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> Instalatora.

```console
installutil /? myAssembly.exe
```

Poniższe polecenie wykonuje składniki instalatora w zestawie `myAssembly.exe`.

```console
installutil myAssembly.exe
```

Następujące polecenie wykonuje składniki instalatora w zestawie przy użyciu przełącznika `/AssemblyName` i w pełni kwalifikowanej nazwy.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę. Należy zauważyć, że wszystkie zestawy określone przez nazwę pliku muszą poprzedzać zestawy określone przez silną nazwę w wierszu polecenia, ponieważ nie można zastąpić opcji `/AssemblyName`.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Następujące polecenie wykonuje składniki dezinstalatora w zestawie `myAssembly.exe`.

```console
installutil /u myAssembly.exe
```

Następujące polecenie wykonuje składniki dezinstalatora w zestawach `myAssembly1.exe` i `myAssembly2.exe`.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Ponieważ pozycja opcji `/u` w wierszu polecenia nie jest ważna, jest to równoznaczne z następującym poleceniem.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Następujące polecenie wykonuje instalatorów w zestawie `myAssembly.exe` i określa, że informacje o postępie będą zapisywane w `myLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Następujące polecenie wykonuje Instalatory w zestawie `myAssembly.exe`, określa, że informacje o postępie powinny być zapisywane do `myLog.InstallLog`i używa opcji niestandardowej `/reg` instalacji, aby określić, że aktualizacje mają zostać wprowadzone do rejestru systemowego.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Następujące polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, używa opcji niestandardowego `/email` Instalatora, aby określić adres e-mail użytkownika i pomija dane wyjściowe do pliku dziennika.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Następujące polecenie zapisuje postęp instalacji `myAssembly.exe`, aby `myLog.InstallLog` i zapisuje postęp `myTestAssembly.exe` do `myTestLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.Install>
- [Narzędzia](index.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
