---
title: Instalowanie języka F#
description: Dowiedz się, F# jak zainstalować program w oparciu o środowisko.
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204871"
---
# <a name="install-f"></a>Zainstaluj program F\#

Program można zainstalować F# na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Instalowanie F# za pomocą programu Visual Studio

Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) po raz pierwszy, najpierw zainstaluje się Instalator programu Visual Studio. Zainstaluj odpowiednią jednostkę SKU programu Visual Studio z Instalatora. Jeśli jest już zainstalowany, kliknij przycisk **Modyfikuj**.

Zobaczysz listę obciążeń. Wybierz pozycję **ASP.NET i programowanie dla sieci Web** , co spowoduje zainstalowanie F# obsługi i platformy .NET Core na potrzeby projektów ASP.NET Core.

Następnie kliknij przycisk **Modyfikuj** w prawym dolnym rogu.  Spowoduje to zainstalowanie wszystkich wybranych elementów. Następnie możesz otworzyć program Visual Studio 2017 z F# obsługą języka, klikając przycisk **Uruchom**.

## <a name="install-f-with-visual-studio-code"></a>Zainstaluj F# przy użyciu Visual Studio Code

Najpierw upewnij się, że masz [zainstalowaną](https://git-scm.com/download) i dostępną usługę git do swojej ścieżki. Można sprawdzić, czy jest poprawnie zainstalowana, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

Następnie zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).

Następnie konieczne będzie zainstalowanie [Visual Studio Code](https://code.visualstudio.com) .

Następnie kliknij ikonę rozszerzenia i wyszukaj ciąg "Ionide":

Jedyną wtyczką wymaganą F# do obsługi w Visual Studio Code jest [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Można jednak zainstalować [Ionide-fałszywych](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , aby uzyskać [fałszywe](https://fake.build/) wsparcie i [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) , aby uzyskać pomoc techniczną [Paket](https://fsprojects.github.io/Paket/) . FAŁSZYWE i Paket są dodatkowymi F# narzędziami społecznościowymi do kompilowania projektów i zarządzania zależnościami.

## <a name="install-f-with-visual-studio-for-mac"></a>Zainstaluj F# przy użyciu Visual Studio dla komputerów Mac

F#Program jest instalowany domyślnie w [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)niezależnie od tego, która konfiguracja została wybrana.

Po zakończeniu instalacji wybierz pozycję "Uruchom program Visual Studio". Możesz również uruchomić ją za poorednictwem wyszukiwania w witrynie macOS.

## <a name="install-f-on-a-build-server"></a>Zainstaluj F# na serwerze kompilacji

Jeśli używasz platformy .NET Core lub .NET Framework za pomocą zestawu .NET SDK, wystarczy zainstalować zestaw .NET SDK na serwerze kompilacji. Ma wszystko, czego potrzebujesz.

Jeśli używasz .NET Framework i **nie** używasz zestawu .NET SDK, musisz zainstalować [Visual Studio Build Tools jednostkę SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) na serwerze z systemem Windows. W instalatorze wybierz pozycję **narzędzia kompilacji klasycznej platformy .NET** , a następnie wybierz składnik  **F# kompilatora** po prawej stronie menu Instalatora.
