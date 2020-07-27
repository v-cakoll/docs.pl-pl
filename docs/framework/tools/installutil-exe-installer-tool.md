---
title: Installutil.exe (Narzędzie instalatora)
description: Użyj Installutil.exe, narzędzie instalatora. To narzędzie umożliwia instalowanie lub odinstalowywanie zasobów serwera przez wykonywanie składników Instalatora w określonych zestawach.
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
ms.openlocfilehash: 042e5f64a7a863173db9c4e601d3152b0df46d97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164440"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Narzędzie instalatora)

Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach. To narzędzie działa w połączeniu z klasami w <xref:System.Configuration.Install> przestrzeni nazw.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Opis|
|--------------|-----------------|
|`assembly`|Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora. Pomiń ten parametr, jeśli chcesz określić silną nazwę zestawu przy użyciu `/AssemblyName` opcji.|

<a name="options"></a>

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/h[elp]`<br /><br /> -lub-<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/help`*zestaw*<br /><br /> -lub-<br /><br /> `/?`*zestaw*|Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe. Ta opcja powoduje dodanie tekstu zwróconego przez każdą właściwość składnika Instalatora <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> do tekstu pomocy InstallUtil.exe.|
|`/AssemblyName`"*AssemblyName*<br /><br /> , Version =*główna. pomocnicza. kompilacja. poprawka*<br /><br /> , Kultura =*Ustawienia regionalne*<br /><br /> , PublicKeyToken =*PublicKeyToken*"|Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu. W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.<br /><br /> Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".|
|`/InstallStateDir=[`*katalogname*`]`|Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu. Domyślnie, jest to katalog, w którym znajduje się zestaw.|
|`/LogFile=`[*filename*]|Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji. Domyślnie, jeśli `/LogFile` opcja zostanie pominięta, plik dziennika o nazwie *AssemblyName*. InstallLog. Jeśli *Nazwa pliku* zostanie pominięta, żaden plik dziennika nie zostanie wygenerowany.|
|`/LogToConsole`= { `true`&#124;`false` }|Jeśli `true` , wyświetla dane wyjściowe w konsoli programu. Jeśli `false` (wartość domyślna), pomija dane wyjściowe w konsoli programu.|
|`/ShowCallStack`|Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.|
|`/u`[`ninstall`]|Odinstalowuje określone zestawy. W przeciwieństwie do innych opcji, `/u` ma zastosowanie do wszystkich zestawów bez względu na to, gdzie opcja pojawia się w wierszu polecenia.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Dodatkowe opcje instalatora

Poszczególne Instalatory używane w ramach zestawu mogą rozpoznawać opcje oprócz tych wymienionych w sekcji [Opcje](#options) . Aby dowiedzieć się więcej na temat tych opcji, uruchom InstallUtil.exe ze ścieżkami zestawów w wierszu polecenia wraz z `/?` `/help` opcją or. Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.

> [!NOTE]
> Tekst pomocy na temat opcji obsługiwanych przez poszczególne składniki instalatora jest zwracany przez <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> Właściwość. Poszczególne opcje, które zostały wprowadzone w wierszu polecenia, są dostępne programowo z <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> właściwości.

Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji. Jeśli jednak użyjesz `/Password` parametru, który jest rozpoznawany przez niektóre składniki instalatora, informacje o haśle zostaną zastąpione przez osiem gwiazdek (*) i nie będą wyświetlane w pliku dziennika.

> [!IMPORTANT]
> W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu. Aby uniknąć tego zachowania, można pominąć plik dziennika, określając `/LogFile=` (bez argumentu *filename* ) po Installutil.exe w wierszu polecenia.

## <a name="remarks"></a>Uwagi

Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji. Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji. Program Installutil.exe wykrywa i wykonuje te składniki instalatora.

W jednym wierszu polecenia można określić wiele zestawów. Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu. Z wyjątkiem `/u` i `/AssemblyName` , opcje są skumulowane, ale Zastąp. Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.

Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:

- InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.

- *AssemblyName*. InstallLog — zawiera informacje specyficzne dla fazy zatwierdzania procesu instalacji. Aby uzyskać więcej informacji na temat fazy zatwierdzania, zobacz <xref:System.Configuration.Install.Installer.Commit%2A> metodę.

- *AssemblyName*. InstallState — zawiera dane używane do odinstalowania zestawu.

Installutil.exe używa odbicia w celu sprawdzenia określonych zestawów i znalezienia wszystkich <xref:System.Configuration.Install.Installer> typów, które mają <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> ustawiony atrybut `true` . Narzędzie wykonuje następnie albo <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metodę dla każdego wystąpienia <xref:System.Configuration.Install.Installer> typu. Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów. Odinstalowanie nie jest transakcyjne.

Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.

Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator. Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL). Obie wersje narzędzia instalatora działają tak samo.

Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++. Jeśli spróbujesz wdrożyć usługę systemu Windows w języku C++ przy użyciu Installutil.exe, zostanie zgłoszony wyjątek, taki jak <xref:System.BadImageFormatException> . Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.

## <a name="examples"></a>Przykłady

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.

```console
installutil /?
```

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe. Wyświetla również opis i listę opcji obsługiwanych przez składniki instalatora w programie, `myAssembly.exe` Jeśli tekst pomocy został przypisany do <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości Instalatora.

```console
installutil /? myAssembly.exe
```

Następujące polecenie wykonuje składniki instalatora w zestawie `myAssembly.exe` .

```console
installutil myAssembly.exe
```

Następujące polecenie wykonuje składniki instalatora w zestawie przy użyciu `/AssemblyName` przełącznika i w pełni kwalifikowanej nazwy.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę. Należy zauważyć, że wszystkie zestawy określone przez nazwę pliku muszą poprzedzać zestawy określone przez silną nazwę w wierszu polecenia, ponieważ `/AssemblyName` nie można zastąpić tej opcji.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Następujące polecenie wykonuje składniki dezinstalatora w zestawie `myAssembly.exe` .

```console
installutil /u myAssembly.exe
```

Następujące polecenie wykonuje składniki dezinstalatora w zestawach `myAssembly1.exe` i `myAssembly2.exe` .

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Ponieważ pozycja `/u` opcji w wierszu polecenia nie jest ważna, jest to równoznaczne z następującym poleceniem.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Następujące polecenie wykonuje Instalatory w zestawie `myAssembly.exe` i określa, w jaki sposób informacje o postępie będą zapisywane `myLog.InstallLog` .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Następujące polecenie wykonuje instalatorów w zestawie `myAssembly.exe` , określa, czy informacje o postępie powinny być zapisywane w programie `myLog.InstallLog` , i używa opcji niestandardowej instalacji, `/reg` Aby określić, że aktualizacje mają zostać wprowadzone do rejestru systemowego.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Następujące polecenie wykonuje Instalatory w zestawie `myAssembly.exe` , używa opcji niestandardowej Instalatora, `/email` Aby określić adres e-mail użytkownika i pomija dane wyjściowe do pliku dziennika.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Następujące polecenie zapisuje postęp instalacji programu do programu `myAssembly.exe` `myLog.InstallLog` i zapisuje postęp dla programu `myTestAssembly.exe` do `myTestLog.InstallLog` .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.Install>
- [Narzędzia](index.md)
- [Wiersze poleceń](developer-command-prompt-for-vs.md)
