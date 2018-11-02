---
title: 'Zainstaluj język F #'
description: 'Dowiedz się, jak zainstalować zależności od używanego środowiska F #.'
ms.date: 08/28/2018
ms.openlocfilehash: d53ecdcba5411db62208cb683a0fad795711b77c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50193906"
---
# <a name="install-f"></a>Zainstaluj język F # #

Można zainstalować F # na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Instalowanie języka F # za pomocą programu Visual Studio

Jeśli masz pobieranie [programu Visual Studio](https://visualstudio.microsoft.com/) po raz pierwszy zostanie najpierw zainstalować Instalatora programu Visual Studio. Zainstaluj odpowiednie jednostki SKU programu Visual Studio z poziomu Instalatora. Jeśli masz już zainstalowany, kliknij przycisk **Modyfikuj**.

Następnie zobaczysz listę obciążeń. Wybierz **ASP.NET i tworzenie aplikacji internetowych** które zainstaluje obsługę F # i .NET Core dla projektów ASP.NET Core.

Następnie kliknij przycisk **Modyfikuj** w dolnym po prawej stronie.  Spowoduje to zainstalowanie wszystko, co jest wybrane. Następnie możesz otworzyć programu Visual Studio 2017 z obsługą języka F #, klikając **Uruchom**.

## <a name="install-f-with-visual-studio-for-mac"></a>Zainstaluj język F # za pomocą programu Visual Studio dla komputerów Mac

F # jest instalowany domyślnie w [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/), niezależnie od tego, która Konfiguracja wybierzesz.

Po zakończeniu instalacji wybierz pozycję "Uruchom Visual Studio". Można również uruchomić go za pomocą wyszukiwania w systemie macOS.

## <a name="install-f-with-visual-studio-code"></a>Instalowanie języka F # za pomocą programu Visual Studio Code

Konieczne jest posiadanie [zainstalowane narzędzie git](https://git-scm.com/download) i dostępne w zmiennej PATH, aby użyć szablonów projektu. Możesz sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Narzędzie mono](https://www.mono-project.com) służy do [F # Interactive](../tutorials/fsharp-interactive/index.md) pomocy technicznej. Najprostszym sposobem zainstalowania platformy Mono w systemie macOS jest za pośrednictwem Homebrew. Po prostu wpisz następujące polecenie w terminalu:

```console
brew install mono
```

Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Narzędzie mono](https://www.mono-project.com) służy do [F # Interactive](../tutorials/fsharp-interactive/index.md) pomocy technicznej. W przypadku systemie Debian lub Ubuntu, można użyć następujących czynności:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Zainstaluj [programu Visual Studio z obsługi języka F #](#install-f-with-visual-studio). Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, skompilowania i wykonania kodu F #.

Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download/).

---

Następnie należy [programu Visual Studio Code](https://code.visualstudio.com) zainstalowane.

Następnie kliknij ikonę rozszerzenia i poszukaj pozycji "Ionide":

Tylko dodatek typu plug-in, wymagana jest obsługa języka F # w programie Visual Studio Code [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) można pobrać [FAŁSZYWE](https://fsharp.github.io/FAKE/) pomocy technicznej i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) można pobrać [Paket](https://fsprojects.github.io/Paket/) pomocy technicznej. FAŁSZYWE i Paket dodatkowych narzędzi społeczności F # do kompilowania projektów i zarządzanie zależnościami, odpowiednio.
