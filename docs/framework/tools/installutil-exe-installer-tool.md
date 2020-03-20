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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105073"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Narzędzie instalatora)

Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach. To narzędzie działa w połączeniu <xref:System.Configuration.Install> z klasami w obszarze nazw.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Opis|
|--------------|-----------------|
|`assembly`|Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora. Pomiń ten parametr, jeśli chcesz określić silną `/AssemblyName` nazwę zestawu za pomocą opcji.|

<a name="options"></a>

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/h[elp]`<br /><br /> — lub —<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/help`*montaż*<br /><br /> — lub —<br /><br /> `/?`*montaż*|Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe. Ta opcja dodaje tekst zwracany przez <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwość każdego składnika instalatora do tekstu pomocy InstallUtil.exe.|
|`/AssemblyName`"*nazwa montażu*<br /><br /> ,Wersja=*major.minor.build.revision*<br /><br /> .Kultura =*ustawienia regionalne*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu. W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.<br /><br /> Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".|
|`/InstallStateDir=[`*nazwa katalogu*`]`|Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu. Domyślnie, jest to katalog, w którym znajduje się zestaw.|
|`/LogFile=`[*nazwa pliku*]|Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji. Domyślnie, jeśli `/LogFile` opcja zostanie pominięta, plik dziennika o nazwie *assemblyname*. InstallLog jest tworzony. Jeśli *nazwa pliku* zostanie pominięta, nie jest generowany żaden plik dziennika.|
|`/LogToConsole`={`true`&#124;`false`}|Jeśli `true`, wyświetla wyjście do konsoli. Jeśli `false` (domyślnie), pomija dane wyjściowe do konsoli.|
|`/ShowCallStack`|Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.|
|`/u`[`ninstall`]|Odinstalowuje określone zestawy. W przeciwieństwie do `/u` innych opcji, stosuje się do wszystkich zestawów, niezależnie od tego, gdzie opcja pojawia się w wierszu polecenia.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Dodatkowe opcje instalatora

Poszczególne instalatory używane w ramach zestawu mogą rozpoznawać opcje oprócz opcji wymienionych w sekcji [Opcje.](#options) Aby dowiedzieć się więcej o tych opcjach, uruchom installUtil.exe ze `/?` ścieżkami zestawów w wierszu polecenia wraz z opcją lub. `/help` Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.

> [!NOTE]
> Tekst pomocy na opcje obsługiwane przez poszczególne składniki <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> instalatora jest zwracany przez właściwość. Poszczególne opcje wprowadzone w wierszu polecenia są dostępne programowo <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> z właściwości.

Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji. Jeśli jednak użyjesz parametru, `/Password` który jest rozpoznawany przez niektóre składniki instalatora, informacje o haśle zostaną zastąpione ośmioma gwiazdkami (*) i nie pojawią się w pliku dziennika.

> [!IMPORTANT]
> W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu. Aby zapobiec takiemu zachowaniu, można pominąć plik dziennika, określając `/LogFile=` (bez argumentu nazwy *pliku)* po installutil.exe w wierszu polecenia.

## <a name="remarks"></a>Uwagi

Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji. Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji. Program Installutil.exe wykrywa i wykonuje te składniki instalatora.

W jednym wierszu polecenia można określić wiele zestawów. Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu. Z `/u` wyjątkiem `/AssemblyName`i , opcje są kumulatywne, ale nadpisywalne. Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.

Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:

- InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.

- *nazwa złożenia*. InstallLog — zawiera informacje specyficzne dla fazy zatwierdzania procesu instalacji. Aby uzyskać więcej informacji na <xref:System.Configuration.Install.Installer.Commit%2A> temat fazy zatwierdzania, zobacz metodę.

- *nazwa złożenia*. InstallState — zawiera dane używane do odinstalowywania zestawu.

Installutil.exe używa odbicia, aby sprawdzić określone zestawy <xref:System.Configuration.Install.Installer> i znaleźć <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> wszystkie typy, które mają atrybut ustawiony na `true`. Narzędzie następnie wykonuje <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> lub <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metody na każdym wystąpieniu <xref:System.Configuration.Install.Installer> typu. Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów. Odinstalowanie nie jest transakcyjne.

Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.

Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator. Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL). Obie wersje narzędzia instalatora działają tak samo.

Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++. Jeśli spróbujesz wdrożyć usługę systemu Windows języka C++ z <xref:System.BadImageFormatException> Installutil.exe, zostanie zgłoszony wyjątek, który zostanie zgłoszony. Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.

## <a name="examples"></a>Przykłady

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.

```console
installutil /?
```

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe. Wyświetla również opis i listę opcji obsługiwanych przez `myAssembly.exe` składniki instalatora, jeśli tekst pomocy został <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> przypisany do właściwości instalatora.

```console
installutil /? myAssembly.exe
```

Następujące polecenie wykonuje składniki instalatora w `myAssembly.exe`złożeniu .

```console
installutil myAssembly.exe
```

Następujące polecenie wykonuje składniki instalatora w złożeniu `/AssemblyName` przy użyciu przełącznika i w pełni kwalifikowanej nazwy.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę. Należy zauważyć, że wszystkie zestawy określone przez nazwę pliku muszą poprzedzać zestawy `/AssemblyName` określone przez silną nazwę w wierszu polecenia, ponieważ nie można zastąpić opcji.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Następujące polecenie wykonuje składniki deinstalatora `myAssembly.exe`w złożeniu .

```console
installutil /u myAssembly.exe
```

Następujące polecenie wykonuje składniki deinstalatora `myAssembly1.exe` w `myAssembly2.exe`złożeniach i .

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Ponieważ położenie `/u` opcji w wierszu polecenia nie jest ważne, jest to równoważne następującej poleceniu.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Następujące polecenie wykonuje instalatorów w `myAssembly.exe` zestawie i określa, że informacje `myLog.InstallLog`o postępie będą zapisywane w pliku .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Następujące polecenie wykonuje instalatorów w `myAssembly.exe`zestawie, określa, że informacje o `myLog.InstallLog`postępie powinny być zapisywane do programu i używa niestandardowej `/reg` opcji instalatorów, aby określić, że aktualizacje powinny być dokonywane w rejestrze systemowym.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Następujące polecenie wykonuje instalatorów w `myAssembly.exe`zestawie, używa niestandardowej `/email` opcji instalatora do określenia adresu e-mail użytkownika i pomija dane wyjściowe do pliku dziennika.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Poniższe polecenie zapisuje postęp `myAssembly.exe` `myLog.InstallLog` instalacji i zapisuje `myTestLog.InstallLog`postęp do `myTestAssembly.exe` .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Configuration.Install>
- [narzędzia](index.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
