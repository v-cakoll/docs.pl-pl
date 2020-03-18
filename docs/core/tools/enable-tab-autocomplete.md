---
title: Włączanie uzupełniania po naciśnięciu tabulatora
description: W tym artykule przedstawiono sposób włączania uzupełniania kart dla funkcji cli programu .NET Core dla programu PowerShell, Bash i zsh.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 31328be14811760bc8d7fb527e0d55abfe6b1493
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156754"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>Jak włączyć uzupełnianie tabu dla cli programu .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

W tym artykule opisano sposób konfigurowania uzupełniania kart dla trzech powłok, programu PowerShell, Bash i zsh. W przypadku innych powłok należy zapoznać się z ich dokumentacją dotyczącą konfigurowania uzupełniania kart.

Po skonfigurowaniu uzupełnianie karty dla wiersza wiersza `dotnet` polecenia .NET Core jest wyzwalane przez wpisanie polecenia w powłoce, a następnie naciśnięcie klawisza TAB. Bieżący wiersz polecenia jest `dotnet complete` wysyłany do polecenia, a wyniki są przetwarzane przez powłokę. Wyniki można przetestować bez włączania uzupełniania kart, wysyłając coś bezpośrednio do `dotnet complete` polecenia. Przykład:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Jeśli to polecenie nie działa, upewnij się, że jest zainstalowany zestaw SDK .NET Core 2.0 lub wyższy. Jeśli jest zainstalowany, ale to polecenie nadal nie działa, `dotnet` upewnij się, że polecenie jest rozpoznawane do wersji .NET Core 2.0 SDK i powyżej. Użyj `dotnet --version` polecenia, aby zobaczyć, jaka wersja bieżącej `dotnet` ścieżki jest rozpoznawana. Aby uzyskać więcej informacji, zobacz [Wybieranie wersji .NET Core do użycia](../versions/selection.md).

### <a name="examples"></a>Przykłady

Oto kilka przykładów tego, co zapewnia uzupełnianie kart:

Dane wejściowe                                | Staje się                                                                     | , ponieważ klienci usługi
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add`jest pierwszym podpoleceniem, alfabetycznie.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Uzupełnianie kart pasuje `--help` do podciągów i jest na pierwszym miejscu alfabetycznie.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Naciśnięcie karty po raz drugi powoduje wyświetlenie następnej sugestii.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Wyniki są zwracane alfabetycznie.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Ukończenie karty jest świadome pliku projektu.

## <a name="powershell"></a>PowerShell

Aby dodać uzupełnianie kart do **programu PowerShell** dla procesora CLI .NET Core, utwórz lub edytuj profil przechowywany w zmiennej `$PROFILE`. Aby uzyskać więcej informacji, zobacz [Jak utworzyć profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) i profile i zasady [wykonywania](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).

Dodaj następujący kod do swojego profilu:

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>bash

Aby dodać uzupełnianie kart do powłoki **bash** dla procesora CLI .NET Core, dodaj do pliku `.bashrc` następujący kod:

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>Zsh

Aby dodać uzupełnianie kart do powłoki **zsh** dla cli .NET Core, dodaj następujący kod do pliku: `.zshrc`

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
