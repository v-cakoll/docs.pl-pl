---
title: Włącz uzupełnianie kart
description: W tym artykule opisano, jak włączyć uzupełnianie kart dla interfejs wiersza polecenia platformy .NET Core dla programu PowerShell, bash i ZSH.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 8c5d6a254db5ba21417ba45122ed0d7cb093c7c3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739316"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>Jak włączyć uzupełnianie kart dla interfejs wiersza polecenia platformy .NET Core

Począwszy od zestawu SDK platformy .NET Core 2,0, interfejs wiersza polecenia platformy .NET Core obsługuje uzupełnianie kart. W tym artykule opisano sposób konfigurowania uzupełniania tabulatorów dla trzech powłok, programu PowerShell, bash i ZSH. Inne powłoki mogą obsługiwać Autouzupełnianie. Zapoznaj się z dokumentacją dotyczącą sposobu konfigurowania automatycznego uzupełniania, kroki powinny być podobne do kroków opisanych w tym artykule.

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

Po zakończeniu instalacji zostanie wyzwolone zakończenie karty interfejs wiersza polecenia platformy .NET Core, wpisując `dotnet` polecenie w powłoce, a następnie naciskając klawisz TAB. Bieżący wiersz polecenia jest wysyłany do polecenia `dotnet complete`, a wyniki są przetwarzane przez powłokę. Wyniki można testować bez włączania kończenia karty, wysyłając coś bezpośrednio do `dotnet complete` polecenia. Na przykład:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Jeśli to polecenie nie działa, upewnij się, że jest zainstalowany zestaw .NET Core 2,0 SDK lub nowszy. Jeśli jest zainstalowana, ale to polecenie nadal nie działa, upewnij się, że polecenie `dotnet` jest rozpoznawane jako wersja zestawu SDK platformy .NET Core 2,0 i nowszych. Użyj `dotnet --version` polecenia, aby sprawdzić, która wersja `dotnet` Twoja bieżąca ścieżka jest rozpoznawana. Aby uzyskać więcej informacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md).

### <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów zapewniania przez uzupełnianie kart:

Dane wejściowe                                | stanowi                                                                     | ponieważ
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` to pierwszy podpolecenie, alfabetycznie.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Uzupełnianie tabulacji dopasowuje podciągi, a `--help` są w kolejności alfabetycznej.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Naciśnięcie klawisza Tab drugi raz spowoduje wyświetlenie następnej sugestii.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Wyniki są zwracane w porządku alfabetycznym.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Uzupełnianie karty jest świadome pliku projektu.

## <a name="powershell"></a>PowerShell

Aby dodać uzupełnianie tabulatorów do **programu PowerShell** dla interfejs wiersza polecenia platformy .NET Core, Utwórz lub Edytuj profil zapisany w zmiennej `$PROFILE`. Aby uzyskać więcej informacji, zobacz [jak utworzyć profil](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) i [zasady wykonywania](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy). 

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

Aby dodać uzupełnianie karty do powłoki **bash** dla interfejs wiersza polecenia platformy .NET Core, Dodaj następujący kod do pliku `.bashrc`:

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

## <a name="zsh"></a>zsh

Aby dodać uzupełnianie karty do powłoki **ZSH** dla interfejs wiersza polecenia platformy .NET Core, Dodaj następujący kod do pliku `.zshrc`:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
