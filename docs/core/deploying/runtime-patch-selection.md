---
title: Środowisko uruchomieniowe przenoszenia do przodu dla platformy .NET Core aplikację samodzielną wdrożeń.
description: Dowiedz się więcej o dotnet publikowania zmian w przypadku wdrożeń niezależna.
author: jralexander
ms.author: kdollard
ms.date: 05/31/2018
ms.custom: seodec18
ms.openlocfilehash: dde00cf71f0d67c8c4380748e01a4ef5c17ebb4a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126682"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Niezależne wdrożenia środowiska uruchomieniowego przenoszenia do przodu

.NET core [niezależna acji](index.md) biblioteki .NET Core i środowisko uruchomieniowe platformy .NET Core. Począwszy od .NET Core 2.1 SDK (wersja 2.1.300), wdrożenie aplikacji niezależna [publikuje najwyższy runtime poprawki na swojej maszynie](https://github.com/dotnet/designs/pull/36). Domyślnie [ `dotnet publish` ](../tools/dotnet-publish.md) dla wdrożenia niezależna wybiera najnowszej wersji, instalowany jako część zestawu SDK na maszynie publikowania. Dzięki temu Twojej wdrożonej aplikacji do uruchamiania przy użyciu poprawek zabezpieczeń (i inne poprawki) dostępnych w trakcie `publish`. Aplikacja musi być opublikowany ponownie w celu uzyskania nowych poprawek. Aplikacje samodzielne są tworzone przez określenie `-r <RID>` na `dotnet publish` polecenia lub określając [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) w pliku projektu (csproj / vbproj) lub w wierszu polecenia.

## <a name="patch-version-roll-forward-overview"></a>Omówienie do przodu roll wersja poprawki

[`restore`](../tools/dotnet-restore.md), [ `build` ](../tools/dotnet-build.md) i [ `publish` ](../tools/dotnet-publish.md) są `dotnet` poleceń, które można uruchomić osobno. Wybór środowiska uruchomieniowego jest częścią `restore` operacji nie `publish` lub `build`. Jeśli wywołasz `publish`, najnowsza wersja poprawki zostanie wybrany. Jeśli wywołasz `publish` z `--no-restore` argumentu, możesz nie zawierają wersji poprawki żądaną ponieważ wcześniej `restore` nie mogło zostać wykonane za pomocą nowej aplikacji niezależna publikowania zasad. W tym przypadku błąd kompilacji jest generowany z tekstem podobny do następującego:

  "Projektu zostało przywrócone, za pomocą wersji 2.0.0 pakietów Microsoft.NETCore.App, ale z bieżącymi ustawieniami wersji 2.0.6 będzie używana zamiast tego. Aby rozwiązać ten problem, upewnij się, że te same ustawienia są stosowane do przywracania i kolejne operacje, takie jak kompilacja lub opublikować. Zazwyczaj ten problem może wystąpić, jeśli RuntimeIdentifier zostaje ustalona podczas tworzenia lub opublikować, ale nie podczas przywracania."

> [!NOTE]
> `restore` i `build` mogą być uruchamiane niejawnie jako część innego polecenia, takie jak `publish`. Po uruchomieniu niejawnie jako część innego polecenia, są one wyposażone dodatkowy kontekst, aby odpowiednie artefakty są tworzone. Gdy możesz `publish` aparatu plików wykonywalnych (na przykład `dotnet publish -r linux-x64`), niejawny `restore` przywraca pakietów dla środowiska uruchomieniowego x64 systemu linux. Jeśli wywołasz `restore` jawnie, nie są przywracane pakiety środowiska uruchomieniowego domyślnie, ponieważ nie ma tego kontekstu.

## <a name="how-to-avoid-restore-during-publish"></a>Jak unikać przywracania podczas publikowania

Uruchamianie `restore` jako część `publish` operacji może być niepożądane dla danego scenariusza. Aby uniknąć `restore` podczas `publish` podczas tworzenia aplikacji niezależna, wykonaj następujące czynności:

* Ustaw `RuntimeIdentifiers` właściwość rozdzieloną średnikami listę wszystkich [RID](../rid-catalog.md) do opublikowania.
* Ustaw `TargetLatestRuntimePatch` właściwość `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Opcje publikowania argument bez przywracania za pomocą polecenia dotnet

Jeśli chcesz tworzyć aplikacje zarówno niezależna i [zależny od struktury aplikacji](index.md) przy użyciu tego samego pliku projektu, i chcesz używać `--no-restore` argumentu `dotnet publish`, a następnie wybierz jedno z następujących czynności:

1. Preferuj zachowań zależnych od framework. Jeśli aplikacja jest zależny od struktury, jest to zachowanie domyślne. Jeśli aplikacja jest niezależna i można używać bez 2.1.0 lokalne środowisko uruchomieniowe, ustaw `TargetLatestRuntimePatch` do `false` w pliku projektu.

2. Preferuj niezależna zachowanie. Jeśli aplikacja jest niezależny, jest to zachowanie domyślne. Jeśli aplikacja jest zależny od struktury i wymaga Najnowsza zainstalowana poprawka, ustaw `TargetLatestRuntimePatch` do `true` w pliku projektu.

3. Wykonaj jawną kontrolę framework w wersji środowiska uruchomieniowego, ustawiając `RuntimeFrameworkVersion` do wersji poprawki określonych w pliku projektu.
