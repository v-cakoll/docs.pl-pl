---
title: Instalowanie języka F#
description: Dowiedz się, F# jak zainstalować program na różne sposoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346565"
---
# <a name="install-f"></a>Zainstaluj program F\#

Program można zainstalować F# na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Instalowanie F# za pomocą programu Visual Studio

1. Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) po raz pierwszy, najpierw zainstaluje Instalator programu Visual Studio. Zainstaluj odpowiednią wersję programu Visual Studio z Instalatora.

   Jeśli masz już zainstalowany program Visual Studio, wybierz pozycję **Modyfikuj** obok wersji, która ma zostać dodana F# .

2. Na stronie obciążenia wybierz obciążenie **ASP.NET i sieci Web** , F# w tym obsługę platformy .net core dla projektów ASP.NET Core.

3. Wybierz pozycję **Modyfikuj** w prawym dolnym rogu, aby zainstalować wszystkie wybrane elementy.

   Następnie możesz otworzyć program Visual Studio F# , wybierając pozycję **Uruchom** w Instalator programu Visual Studio.

## <a name="install-f-with-visual-studio-code"></a>Zainstaluj F# przy użyciu Visual Studio Code

1. Upewnij się, że masz zainstalowaną i dostępną usługę [git](https://git-scm.com/download) do swojej ścieżki. Można sprawdzić, czy jest poprawnie zainstalowana, wprowadzając `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

2. Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download) i [Visual Studio Code](https://code.visualstudio.com).

3. Wybierz ikonę rozszerzenia i wyszukaj ciąg "Ionide":

   Jedyną wtyczką wymaganą F# do obsługi w Visual Studio Code jest [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Można jednak zainstalować [Ionide-fałszywych](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , aby uzyskać [fałszywe](https://fake.build/) wsparcie i [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) , aby uzyskać pomoc techniczną [Paket](https://fsprojects.github.io/Paket/) . FAŁSZYWE i Paket są dodatkowymi F# narzędziami społecznościowymi do kompilowania projektów i zarządzania zależnościami.

## <a name="install-f-with-visual-studio-for-mac"></a>Zainstaluj F# przy użyciu Visual Studio dla komputerów Mac

F#Program jest instalowany domyślnie w [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)niezależnie od tego, która konfiguracja została wybrana.

Po zakończeniu instalacji wybierz pozycję **Uruchom program Visual Studio**. Program Visual Studio można także otworzyć w programie macOS.

## <a name="install-f-on-a-build-server"></a>Zainstaluj F# na serwerze kompilacji

Jeśli używasz platformy .NET Core lub .NET Framework za pomocą zestawu .NET SDK, wystarczy zainstalować zestaw .NET SDK na serwerze kompilacji. Ma wszystko, czego potrzebujesz.

Jeśli używasz .NET Framework i **nie** używasz zestawu .NET SDK, musisz zainstalować [Visual Studio Build Tools jednostkę SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) na serwerze z systemem Windows. W instalatorze wybierz pozycję **narzędzia kompilacji klasycznej platformy .NET**, a następnie wybierz składnik  **F# kompilatora** po prawej stronie menu Instalatora.
