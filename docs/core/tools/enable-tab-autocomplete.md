---
title: Włączanie uzupełniania po naciśnięciu tabulatora
description: Ten artykuł nauczy Cię sposobu włączania uzupełniania po naciśnięciu tabulatora dla platformy .NET Core interfejsu wiersza polecenia programu PowerShell, Bash i zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 16574e02aa9f9167602401eef2ad7a73e07ad107
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203340"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="b94ff-103">Jak włączyć uzupełnianie po naciśnięciu TABULATORA dla wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b94ff-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="b94ff-104">Począwszy od programu .NET Core 2.0 SDK, interfejsu wiersza polecenia platformy .NET Core obsługuje uzupełnianie po naciśnięciu tabulatora.</span><span class="sxs-lookup"><span data-stu-id="b94ff-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="b94ff-105">W tym artykule opisano sposób konfigurowania uzupełniania po naciśnięciu tabulatora dla trzech powłoki, programu PowerShell, Bash i zsh.</span><span class="sxs-lookup"><span data-stu-id="b94ff-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="b94ff-106">Inne powłoki mogą mieć obsługę funkcji autouzupełniania.</span><span class="sxs-lookup"><span data-stu-id="b94ff-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="b94ff-107">Zobacz ich dokumentację na temat konfigurowania funkcji autouzupełniania, kroki powinny być podobne do czynności opisanych w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="b94ff-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="b94ff-108">Po instalacji uzupełniania po naciśnięciu tabulatora dla interfejsu wiersza polecenia platformy .NET Core jest wyzwalany przez wpisanie `dotnet` polecenie w powłoce, a następnie naciskając klawisz TAB.</span><span class="sxs-lookup"><span data-stu-id="b94ff-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="b94ff-109">Bieżący wiersz polecenia są wysyłane do `dotnet complete` polecenia, a wyniki są przetwarzane przez powłoki.</span><span class="sxs-lookup"><span data-stu-id="b94ff-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="b94ff-110">Wyniki można przetestować bez włączania uzupełniania po naciśnięciu tabulatora, wysyłając coś bezpośrednio do `dotnet complete` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b94ff-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="b94ff-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b94ff-111">For example:</span></span>

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="b94ff-112">Jeśli polecenie nie działa, upewnij się, że zestaw .NET Core 2.0 SDK lub powyżej jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="b94ff-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="b94ff-113">Jeśli jest zainstalowany, ale polecenie nie działa, upewnij się, że `dotnet` polecenie usuwa do wersji programu .NET Core 2.0 SDK lub jego nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="b94ff-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="b94ff-114">Użyj `dotnet --version` polecenie, aby zobaczyć bieżącą wersję programu `dotnet` Twojej bieżącej ścieżki jest rozpoznawana.</span><span class="sxs-lookup"><span data-stu-id="b94ff-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="b94ff-115">Aby uzyskać więcej informacji, zobacz [wybierz wersję platformy .NET Core do użycia](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="b94ff-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="b94ff-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b94ff-116">Examples</span></span>

<span data-ttu-id="b94ff-117">Poniżej przedstawiono kilka przykładów zawiera jakie uzupełniania po naciśnięciu tabulatora:</span><span class="sxs-lookup"><span data-stu-id="b94ff-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="b94ff-118">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="b94ff-118">Input</span></span>                                | <span data-ttu-id="b94ff-119">staje się</span><span class="sxs-lookup"><span data-stu-id="b94ff-119">becomes</span></span>                                                                     | <span data-ttu-id="b94ff-120">ponieważ</span><span class="sxs-lookup"><span data-stu-id="b94ff-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="b94ff-121">`add` to pierwszy podpolecenia alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="b94ff-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="b94ff-122">Karta uzupełniania dopasowań podciągów i `--help` wykorzystasz w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="b94ff-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="b94ff-123">Naciśnięcie klawisza tab po raz drugi wyświetlenie sugestią dalej.</span><span class="sxs-lookup"><span data-stu-id="b94ff-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="b94ff-124">Wyniki są zwracane w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="b94ff-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="b94ff-125">Uzupełnianie po naciśnięciu tabulatora jest świadomość pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b94ff-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="b94ff-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b94ff-126">PowerShell</span></span>

<span data-ttu-id="b94ff-127">Aby dodać uzupełniania po naciśnięciu tabulatora, aby **PowerShell** dla platformy .NET Core interfejsu wiersza polecenia, należy utworzyć lub edytować profilu przechowywana w zmiennej `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="b94ff-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="b94ff-128">Aby uzyskać więcej informacji, zobacz [jak utworzyć swój profil](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) i [profile i zasady wykonywania](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="b94ff-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="b94ff-129">Dodaj następujący kod do Twojego profilu:</span><span class="sxs-lookup"><span data-stu-id="b94ff-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="b94ff-130">Bash</span><span class="sxs-lookup"><span data-stu-id="b94ff-130">Bash</span></span>

<span data-ttu-id="b94ff-131">Uzupełnianie po naciśnięciu tabulatora, aby dodać swoje **bash** powłoki interfejsu wiersza polecenia platformy .NET Core, Dodaj następujący kod, aby Twoje `.bashrc` pliku:</span><span class="sxs-lookup"><span data-stu-id="b94ff-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="b94ff-132">zsh</span><span class="sxs-lookup"><span data-stu-id="b94ff-132">Zsh</span></span>

<span data-ttu-id="b94ff-133">Uzupełnianie po naciśnięciu tabulatora, aby dodać swoje **zsh** powłoki interfejsu wiersza polecenia platformy .NET Core, Dodaj następujący kod, aby Twoje `.zshrc` pliku:</span><span class="sxs-lookup"><span data-stu-id="b94ff-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
