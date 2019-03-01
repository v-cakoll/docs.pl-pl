---
title: ZainstalujF#
description: Dowiedz się, jak zainstalować F# zależności od używanego środowiska.
ms.date: 08/28/2018
ms.openlocfilehash: 873d3021ba884ec81992469e5d0f3b7c18b1e0f4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975254"
---
# <a name="install-f"></a>Zainstaluj F\#

Możesz zainstalować F# na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Zainstaluj F# za pomocą programu Visual Studio

Jeśli masz pobieranie [programu Visual Studio](https://visualstudio.microsoft.com/) po raz pierwszy zostanie najpierw zainstalować Instalatora programu Visual Studio. Zainstaluj odpowiednie jednostki SKU programu Visual Studio z poziomu Instalatora. Jeśli masz już zainstalowany, kliknij przycisk **Modyfikuj**.

Następnie zobaczysz listę obciążeń. Wybierz **ASP.NET i tworzenie aplikacji internetowych** które zainstaluje F# pomocy technicznej i .NET Core obsługuje dla projektów ASP.NET Core.

Następnie kliknij przycisk **Modyfikuj** w dolnym po prawej stronie.  Spowoduje to zainstalowanie wszystko, co jest wybrane. Następnie możesz otworzyć Visual Studio 2017 z F# języki, klikając **Uruchom**.

## <a name="install-f-with-visual-studio-for-mac"></a>Zainstaluj F# z programem Visual Studio dla komputerów Mac

F#jest instalowany domyślnie w [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/), niezależnie od tego, która Konfiguracja wybierzesz.

Po zakończeniu instalacji wybierz pozycję "Uruchom Visual Studio". Można również uruchomić go za pomocą wyszukiwania w systemie macOS.

## <a name="install-f-with-visual-studio-code"></a>Zainstaluj F# za pomocą programu Visual Studio Code

Konieczne jest posiadanie [zainstalowane narzędzie git](https://git-scm.com/download) i dostępne w zmiennej PATH, aby użyć szablonów projektu. Możesz sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Narzędzie mono](https://www.mono-project.com) służy do [ F# Interactive](../tutorials/fsharp-interactive/index.md) pomocy technicznej. Najprostszym sposobem zainstalowania platformy Mono w systemie macOS jest za pośrednictwem Homebrew. Po prostu wpisz następujące polecenie w terminalu:

```console
brew install mono
```

Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Narzędzie mono](https://www.mono-project.com) służy do [ F# Interactive](../tutorials/fsharp-interactive/index.md) pomocy technicznej. W przypadku systemie Debian lub Ubuntu, można użyć następujących czynności:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Zainstaluj [programu Visual Studio z F# obsługuje](#install-f-with-visual-studio). Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, skompilowania i wykonania F# kodu.

Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download/).

---

Następnie należy [programu Visual Studio Code](https://code.visualstudio.com) zainstalowane.

Następnie kliknij ikonę rozszerzenia i poszukaj pozycji "Ionide":

Wtyczka tylko wymagane dla F# pomoc techniczna w Visual Studio Code jest [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) można pobrać [FAŁSZYWE](https://fsharp.github.io/FAKE/) pomocy technicznej i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) można pobrać [Paket](https://fsprojects.github.io/Paket/) pomocy technicznej. FAŁSZYWE i Paket są naliczane dodatkowo F# narzędzia społeczności do kompilowania projektów i zarządzanie zależnościami, odpowiednio.
