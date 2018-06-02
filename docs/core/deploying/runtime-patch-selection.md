---
title: Samodzielne wdrożenia środowiska uruchomieniowego przenoszenia do przodu
description: Dowiedz się więcej o dotnet Opublikuj zmiany wdrożeń niezależne.
author: jralexander
ms.author: kdollard
ms.date: 05/31/2018
ms.openlocfilehash: 40d28e81e2ac1b27e7fd89e16d2d906a080fd18b
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697251"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Samodzielne wdrożenia środowiska uruchomieniowego przenoszenia do przodu

Oprogramowanie .NET core [wdrożeń aplikację autonomiczną](index.md) obejmujące bibliotek .NET Core i środowiska uruchomieniowego .NET Core. W programie .NET Core SDK 2.1.300 (.NET Core 2.1) wdrożenia aplikację autonomiczną [teraz publikuje najwyższy środowiska uruchomieniowego poprawki na komputerze](https://github.com/dotnet/designs/pull/36). Domyślnie[ `dotnet publish` ](../tools/dotnet-publish.md) dla wdrożenia niezależne wybiera najnowszej wersji instalowane jako część zestawu SDK na maszynie publikowania. Dzięki temu wdrożonej aplikacji do uruchamiania z poprawki zabezpieczeń (i inne poprawki) dostępnych w trakcie `publish`. Aplikacja musi być opublikowany ponownie, aby uzyskać nowe poprawki. Samodzielne aplikacje zostały utworzone przez określenie `-r <RID>` na `dotnet publish` polecenia lub określając [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) w pliku projektu (csproj / vbproj) lub w wierszu polecenia.

## <a name="patch-version-roll-forward-overview"></a>Poprawka do przodu omówienie zbiorczego wersji

[`restore`](../tools/dotnet-restore.md), [ `build` ](../tools/dotnet-build.md) i [ `publish` ](../tools/dotnet-publish.md) są `dotnet` poleceń, które można uruchomić osobno. Wybór środowiska uruchomieniowego jest częścią `restore` operacji, nie `publish` lub `build`. Jeśli należy wywołać `publish`, zostanie wybrana najnowszej wersji poprawki. Jeśli wywołujesz `publish` z `--no-restore` argumentu, możesz nie zawierają wersji poprawki żądaną ponieważ wcześniej `restore` nie mogło zostać wykonane z nową aplikację autonomiczną publikowania zasad. W takim przypadku błąd kompilacji jest generowany z tekstem podobny do następującego:

  "Projekt został przywrócony przy użyciu Microsoft.NETCore.App wersji 2.0.0, ale z bieżącymi ustawieniami 2.0.6 będą używać wersji zamiast tego. Aby rozwiązać ten problem, upewnij się, że te same ustawienia są stosowane do przywracania i dla kolejnych operacji, takich jak kompilacji lub publikowania. Zazwyczaj ten problem może wystąpić w przypadku RuntimeIdentifier właściwość jest ustawiona podczas kompilacji lub opublikować, ale nie podczas przywracania."

> [!NOTE]
> `restore` i `build` mogą być uruchamiane niejawnie jako część innego polecenia, takie jak `publish`. Uruchom niejawnie jako część innego polecenia, są udostępniane z dodatkowy kontekst w, prawy artefakty są tworzone. Gdy można `publish` o środowisku uruchomieniowym (na przykład `dotnet publish -r linux-x64`), niejawne `restore` przywraca pakietów dla środowiska uruchomieniowego linux x64. Jeśli należy wywołać `restore` jawnie, nie są przywracane pakietów środowiska uruchomieniowego domyślnie, ponieważ nie ma w tym kontekście.

## <a name="how-to-avoid-restore-during-publish"></a>Jak uniknąć Przywracanie podczas publikowania

Uruchomiona `restore` jako część `publish` operacji może być niepożądane dla danego scenariusza. Aby uniknąć `restore` podczas `publish` podczas tworzenia aplikacji niezależne, wykonaj następujące czynności:

* Ustaw `RuntimeIdentifiers` właściwości rozdzieloną średnikami listę wszystkich [identyfikatorów RID](../rid-catalog.md) do opublikowania
* Ustaw `TargetLatestRuntimePatch` właściwości `true`

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Opcje publikowania przywracania nie argumentu z dotnet

Jeśli chcesz utworzyć obie aplikacje niezależna i [aplikacje zależne od framework](index.md) z tego samego pliku projektu, i chcesz użyć `--no-restore` argumentu z `dotnet publish`, a następnie wybierz jedno z następujących czynności:

1. Preferowane jest zachowanie framework zależne. Jeśli aplikacja jest zależne od framework, to zachowanie domyślne. Jeśli aplikacja jest niezależna i można używać bez poprawki 2.1.0 lokalnego środowiska uruchomieniowego, ustaw `TargetLatestRuntimePatch` do `false` w pliku projektu (csproj / vbproj).

2. Preferowane jest niezależna zachowanie. Jeśli aplikacja jest niezależne, to domyślne zachowanie. Jeśli aplikacja jest zależny od framework i wymaga najnowszej zainstalowana poprawka, ustaw `TargetLatestRuntimePatch` do `true` w pliku projektu (csproj / vbproj).

3. Kontrolować jawne framework w wersji środowiska uruchomieniowego przez ustawienie `RuntimeFrameworkVersion` do wersji poprawki określonych w pliku projektu (csproj / vbproj).