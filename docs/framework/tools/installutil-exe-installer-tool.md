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
ms.openlocfilehash: 04074c8120ad2bc4e279ca0c60624bde9d5e42d9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496700"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (Narzędzie instalatora)

Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach. To narzędzie działa w połączeniu z klasami <xref:System.Configuration.Install> przestrzeni nazw.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Opis|
|--------------|-----------------|
|`assembly`|Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora. Pominięcie tego parametru, jeśli chcesz określić silną nazwę zestawu przy użyciu `/AssemblyName` opcji.|

<a name="options"></a>

## <a name="options"></a>Opcje

|Opcja|Opis|
|------------|-----------------|
|`/h[elp]`<br /><br /> —lub—<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/help` *Zestaw*<br /><br /> —lub—<br /><br /> `/?` *Zestaw*|Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe. Ta opcja dodaje tekst zwracany przez każdego składnika Instalatora <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości tekstu Pomocy programu InstallUtil.exe.|
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> , Culture =*ustawień regionalnych*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu. W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.<br /><br /> Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".|
|`/InstallStateDir=[` *directoryName* `]`|Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu. Domyślnie, jest to katalog, w którym znajduje się zestaw.|
|`/LogFile=`[*filename*]|Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji. Domyślnie jeśli `/LogFile` opcja zostanie pominięta, plik dziennika o nazwie *assemblyname*. InstallLog zostanie utworzony. Jeśli *filename* jest pominięty, plik dziennika nie jest generowany.|
|`/LogToConsole`={`true`&#124;`false`}|Jeśli `true`, wyświetla dane wyjściowe do konsoli. Jeśli `false` (ustawienie domyślne), pomija dane wyjściowe do konsoli.|
|`/ShowCallStack`|Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.|
|`/u`[`ninstall`]|Odinstalowuje określone zestawy. W przeciwieństwie do innych opcji `/u` ma zastosowanie do wszystkich zestawów, niezależnie od tego, gdzie jest dostępna w wierszu polecenia.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Dodatkowe opcje instalatora

Poszczególne instalatory używane w obrębie zestawu mogą rozpoznawać dodatkowe opcje oprócz tych wymienionych w [opcje](#options) sekcji. Aby dowiedzieć się więcej na temat tych opcji, uruchom InstallUtil.exe przy użyciu ścieżki zestawów oraz w wierszu polecenia wraz z `/?` lub `/help` opcji. Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.

> [!NOTE]
> Tekst pomocy dotyczącej opcji obsługiwanych przez poszczególne składniki Instalatora jest zwracany przez <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości. Poszczególne opcje, które zostały wprowadzone w wierszu polecenia są dostępne programowo z <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> właściwości.

Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji. Jednak jeśli używasz `/Password` parametr, który jest rozpoznawany przez niektóre składniki Instalatora, informacje hasła zostaną zastąpione ośmioma gwiazdkami (*), a nie będą widoczne w pliku dziennika.

> [!IMPORTANT]
> W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu. Aby temu zapobiec, można pominąć w pliku dziennika, określając `/LogFile=` (bez *filename* argument) po Installutil.exe w wierszu polecenia.

## <a name="remarks"></a>Uwagi

Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji. Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji. Program Installutil.exe wykrywa i wykonuje te składniki instalatora.

W jednym wierszu polecenia można określić wiele zestawów. Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu. Z wyjątkiem `/u` i `/AssemblyName`, opcje są kumulatywne, ale możliwym do zastąpienia. Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.

Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:

- InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.

- *AssemblyName*. InstallLog — zawiera informacje, które są specyficzne dla fazy zatwierdzania procesu instalacji. Aby uzyskać więcej informacji dotyczących fazy zatwierdzania, zobacz <xref:System.Configuration.Install.Installer.Commit%2A> metody.

- *AssemblyName*. Stan — zawiera dane używane do odinstalowywania zestawu.

Installutil.exe używa odbicia w celu sprawdzenia określonych zestawów i znalezienia wszystkich <xref:System.Configuration.Install.Installer> typy, które mają <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> ustawioną wartość atrybutu `true`. Następnie to narzędzie wykonuje <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> lub <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metody dla każdego wystąpienia <xref:System.Configuration.Install.Installer> typu. Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów. Odinstalowanie nie jest transakcyjne.

Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.

Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator. Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL). Obie wersje narzędzia instalatora działają tak samo.

Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++. Jeśli zostanie podjęta próba wdrożenia usługi Windows C++ za pomocą Installutil.exe, wyjątek takich jak <xref:System.BadImageFormatException> zostanie zgłoszony. Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.

## <a name="examples"></a>Przykłady

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.

```console
installutil /?
```

Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe. Wyświetla również opis i listę opcji obsługiwanych przez składniki Instalatora w `myAssembly.exe` Jeżeli tekst pomocy został przypisany do Instalatora programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości.

```console
installutil /? myAssembly.exe
```

Poniższe polecenie wykonuje składniki Instalatora w zestawie `myAssembly.exe`.

```console
installutil myAssembly.exe
```

Poniższe polecenie wykonuje składniki Instalatora w zestawie, używając `/AssemblyName` przełącznika i w pełni kwalifikowanej nazwy.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę. Należy pamiętać, że wszystkie zestawy określone przez nazwę pliku muszą poprzedzać zestawy określone przez silną nazwę w wierszu polecenia, ponieważ `/AssemblyName` nie można zastępować opcji.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Poniższe polecenie wykonuje składniki dezinstalatora w zestawie `myAssembly.exe`.

```console
installutil /u myAssembly.exe
```

Poniższe polecenie wykonuje składniki dezinstalatora w zestawach `myAssembly1.exe` i `myAssembly2.exe`.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Ponieważ pozycja `/u` opcji w wierszu polecenia nie jest ważna, jest to odpowiednik następującego polecenia.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Poniższe polecenie wykonuje instalatorów w zestawie `myAssembly.exe` i określa, że informacje o postępie będą zapisywane do `myLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Poniższe polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, określa, że informacje o postępie będą zapisywane w `myLog.InstallLog`i używa niestandardowego Instalatora `/reg` opcję, aby określić, czy mają zostać wprowadzone aktualizacje systemu rejestr.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Poniższe polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, używa Instalator użytkownika niestandardowego `/email` opcji, aby określić adres e-mail użytkownika i pomija wysyłanie danych wyjściowych do pliku dziennika.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Poniższe polecenie zapisuje postęp instalacji `myAssembly.exe` do `myLog.InstallLog` i zapisuje Postęp dotyczący `myTestAssembly.exe` do `myTestLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.Install>
- [Narzędzia](../../../docs/framework/tools/index.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
