---
title: Instalowanie języka F#
description: Dowiedz się, jak zainstalować F# na różne sposoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400247"
---
# <a name="install-f"></a>Instalacja F\#

F# można zainstalować na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Instalowanie języka F# za pomocą programu Visual Studio

1. Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) po raz pierwszy, najpierw zainstaluje Instalator programu Visual Studio. Zainstaluj odpowiednią wersję programu Visual Studio z instalatora.

   Jeśli masz już zainstalowany program Visual Studio, wybierz **pozycję Modyfikuj** obok wersji, do której chcesz dodać F#.

2. Na stronie Obciążenia wybierz ASP.NET i obciążenie **programistyczne sieci Web,** które obejmuje obsługę f# i .NET Core dla ASP.NET projektów podstawowych.

3. Wybierz **pozycję Modyfikuj** w prawym dolnym rogu, aby zainstalować wszystko, co wybrano.

   Następnie można otworzyć program Visual Studio z f# wybierając **Uruchom** w Instalatorze programu Visual Studio.

## <a name="install-f-with-visual-studio-code"></a>Instalowanie języka F# za pomocą kodu programu Visual Studio

1. Upewnij się, że [masz zainstalowany git](https://git-scm.com/download) i dostępne na path. Można sprawdzić, czy jest poprawnie zainstalowany, `git --version` wprowadzając w wierszu polecenia i naciskając **klawisz Enter**.

2. Zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download) i [kod programu Visual Studio](https://code.visualstudio.com).

3. Wybierz ikonę Rozszerzenia i wyszukaj hasło "Jonid":

   Jedyną wtyczką wymaganą do obsługi języka F# w kodzie programu Visual Studio jest [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Jednak, można również zainstalować [Ionide-FAKE,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) aby uzyskać [fałszywe](https://fake.build/) wsparcie i [Jonide-Paket,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) aby uzyskać wsparcie [Paket.](https://fsprojects.github.io/Paket/) FAKE i Paket są dodatkowe narzędzia społeczności F# do tworzenia projektów i zarządzania zależnościami, odpowiednio.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalowanie języka F# za pomocą programu Visual Studio dla komputerów Mac

F# jest instalowany domyślnie w [programie Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), niezależnie od wybranej konfiguracji.

Po zakończeniu instalacji wybierz pozycję **Uruchom program Visual Studio**. Program Visual Studio można również otworzyć za pośrednictwem programu Finder w systemie macOS.

## <a name="install-f-on-a-build-server"></a>Instalowanie języka F# na serwerze kompilacji

Jeśli używasz .NET Core lub .NET Framework za pośrednictwem .NET SDK, wystarczy zainstalować .NET SDK na serwerze kompilacji. Ma wszystko, czego potrzebujesz.

Jeśli używasz programu .NET Framework i **nie** używasz sdk .NET, następnie należy zainstalować [visual studio kompilacji narzędzia skudoczli na](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) serwerze Windows Server. W instalatorze wybierz **narzędzia kompilacji pulpitu .NET**, a następnie wybierz składnik **kompilatora F#** po prawej stronie menu instalatora.
