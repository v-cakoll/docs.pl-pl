---
title: Włączanie uzupełniania po naciśnięciu tabulatora
description: Ten artykuł nauczy Cię sposobu włączania uzupełniania po naciśnięciu tabulatora dla platformy .NET Core interfejsu wiersza polecenia programu PowerShell, Bash i zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 16574e02aa9f9167602401eef2ad7a73e07ad107
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648220"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>Jak włączyć uzupełnianie po naciśnięciu TABULATORA dla wiersza polecenia platformy .NET Core

Począwszy od programu .NET Core 2.0 SDK, interfejsu wiersza polecenia platformy .NET Core obsługuje uzupełnianie po naciśnięciu tabulatora. W tym artykule opisano sposób konfigurowania uzupełniania po naciśnięciu tabulatora dla trzech powłoki, programu PowerShell, Bash i zsh. Inne powłoki mogą mieć obsługę funkcji autouzupełniania. Zobacz ich dokumentację na temat konfigurowania funkcji autouzupełniania, kroki powinny być podobne do czynności opisanych w tym artykule.

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

Po instalacji uzupełniania po naciśnięciu tabulatora dla interfejsu wiersza polecenia platformy .NET Core jest wyzwalany przez wpisanie `dotnet` polecenie w powłoce, a następnie naciskając klawisz TAB. Bieżący wiersz polecenia są wysyłane do `dotnet complete` polecenia, a wyniki są przetwarzane przez powłoki. Wyniki można przetestować bez włączania uzupełniania po naciśnięciu tabulatora, wysyłając coś bezpośrednio do `dotnet complete` polecenia. Na przykład:

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Jeśli polecenie nie działa, upewnij się, że zestaw .NET Core 2.0 SDK lub powyżej jest zainstalowany. Jeśli jest zainstalowany, ale polecenie nie działa, upewnij się, że `dotnet` polecenie usuwa do wersji programu .NET Core 2.0 SDK lub jego nowszych wersjach. Użyj `dotnet --version` polecenie, aby zobaczyć bieżącą wersję programu `dotnet` Twojej bieżącej ścieżki jest rozpoznawana. Aby uzyskać więcej informacji, zobacz [wybierz wersję platformy .NET Core do użycia](../versions/selection.md).

### <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów zawiera jakie uzupełniania po naciśnięciu tabulatora:

Dane wejściowe                                | staje się                                                                     | ponieważ
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` to pierwszy podpolecenia alfabetycznie.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Karta uzupełniania dopasowań podciągów i `--help` wykorzystasz w kolejności alfabetycznej.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Naciśnięcie klawisza tab po raz drugi wyświetlenie sugestią dalej.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Wyniki są zwracane w porządku alfabetycznym.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Uzupełnianie po naciśnięciu tabulatora jest świadomość pliku projektu.

## <a name="powershell"></a>PowerShell

Aby dodać uzupełniania po naciśnięciu tabulatora, aby **PowerShell** dla platformy .NET Core interfejsu wiersza polecenia, należy utworzyć lub edytować profilu przechowywana w zmiennej `$PROFILE`. Aby uzyskać więcej informacji, zobacz [jak utworzyć swój profil](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) i [profile i zasady wykonywania](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy). 

Dodaj następujący kod do Twojego profilu:

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>Bash

Uzupełnianie po naciśnięciu tabulatora, aby dodać swoje **bash** powłoki interfejsu wiersza polecenia platformy .NET Core, Dodaj następujący kod, aby Twoje `.bashrc` pliku:

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>zsh

Uzupełnianie po naciśnięciu tabulatora, aby dodać swoje **zsh** powłoki interfejsu wiersza polecenia platformy .NET Core, Dodaj następujący kod, aby Twoje `.zshrc` pliku:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
