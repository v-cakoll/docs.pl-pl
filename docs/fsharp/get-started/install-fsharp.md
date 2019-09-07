---
title: Instalowanie języka F#
description: Dowiedz się, F# jak zainstalować program w oparciu o środowisko.
ms.date: 09/05/2019
ms.openlocfilehash: 18b660ff640904119d63f57405752a14f7673e0c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400720"
---
# <a name="install-f"></a>Zainstaluj program F\#

Program można zainstalować F# na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Instalowanie F# za pomocą programu Visual Studio

Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) po raz pierwszy, najpierw zainstaluje się Instalator programu Visual Studio. Zainstaluj odpowiednią jednostkę SKU programu Visual Studio z Instalatora. Jeśli jest już zainstalowany, kliknij przycisk **Modyfikuj**.

Zobaczysz listę obciążeń. Wybierz pozycję **ASP.NET i programowanie dla sieci Web** , co spowoduje zainstalowanie F# obsługi i platformy .NET Core na potrzeby projektów ASP.NET Core.

Następnie kliknij przycisk **Modyfikuj** w prawym dolnym rogu.  Spowoduje to zainstalowanie wszystkich wybranych elementów. Następnie możesz otworzyć program Visual Studio 2017 z F# obsługą języka, klikając przycisk **Uruchom**.

## <a name="install-f-with-visual-studio-for-mac"></a>Zainstaluj F# przy użyciu Visual Studio dla komputerów Mac

F#Program jest instalowany domyślnie w [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)niezależnie od tego, która konfiguracja została wybrana.

Po zakończeniu instalacji wybierz pozycję "Uruchom program Visual Studio". Możesz również uruchomić ją za poorednictwem wyszukiwania w witrynie macOS.

## <a name="install-f-with-visual-studio-code"></a>Zainstaluj F# przy użyciu Visual Studio Code

Aby można było korzystać z szablonów projektów, na ścieżce musi być zainstalowana i dostępna funkcja [git](https://git-scm.com/download) . Można sprawdzić, czy jest poprawnie zainstalowana, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Narzędzie [mono](https://www.mono-project.com) jest używane na potrzeby [ F# interaktywnej](../tutorials/fsharp-interactive/index.md) obsługi. Najprostszym sposobem instalacji narzędzia mono w systemie macOS jest za pośrednictwem oprogramowania homebrew. Po prostu wpisz następujące elementy w terminalu:

```console
brew install mono
```

Zainstaluj również [zestaw .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

Narzędzie [mono](https://www.mono-project.com) jest używane na potrzeby [ F# interaktywnej](../tutorials/fsharp-interactive/index.md) obsługi. Jeśli korzystasz z programu debian lub Ubuntu, możesz skorzystać z następujących czynności:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Zainstaluj również [zestaw .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Zainstaluj [program Visual Studio F# z obsługą techniczną](#install-f-with-visual-studio). Spowoduje to zainstalowanie wszystkich składników niezbędnych do pisania, kompilowania i wykonywania F# kodu.

Zainstaluj również [zestaw .NET Core SDK](https://www.microsoft.com/net/download/).

---

Następnie konieczne będzie zainstalowanie [Visual Studio Code](https://code.visualstudio.com) .

Następnie kliknij ikonę rozszerzenia i wyszukaj ciąg "Ionide":

Jedyną wtyczką wymaganą F# do obsługi w Visual Studio Code jest [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Można jednak zainstalować [Ionide-fałszywych](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , aby uzyskać [fałszywe](https://fsharp.github.io/FAKE/) wsparcie i [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) , aby uzyskać pomoc techniczną [Paket](https://fsprojects.github.io/Paket/) . FAŁSZYWE i Paket są dodatkowymi F# narzędziami społecznościowymi do kompilowania projektów i zarządzania zależnościami.

## <a name="install-f-on-a-build-server"></a>Zainstaluj F# na serwerze kompilacji

Jeśli używasz platformy .NET Core lub .NET Framework za pomocą zestawu .NET SDK, wystarczy zainstalować zestaw .NET SDK na serwerze kompilacji. Ma wszystko, czego potrzebujesz.

Jeśli używasz .NET Framework i **nie** używasz zestawu .NET SDK, musisz zainstalować [Visual Studio Build Tools jednostkę SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) na serwerze z systemem Windows. W instalatorze wybierz pozycję **narzędzia kompilacji klasycznej platformy .NET** , a następnie wybierz składnik  **F# kompilatora** po prawej stronie menu Instalatora.
