---
title: Przewinięcie środowiska uruchomieniowego do funkcji samodzielnego wdrażania aplikacji platformy .NET Core.
description: Dowiedz się więcej na temat dotnet publish zmian w przypadku wdrożeń samodzielnych.
author: KathleenDollard
ms.date: 05/31/2018
ms.openlocfilehash: 22385c7b5d2bf87755fd51cd6268d21fe3431c74
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740784"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Przenoszenie do przodu w czasie samodzielnego środowiska uruchomieniowego wdrożenia

[Wstępnie zawarte wdrożenia aplikacji](index.md) .NET Core obejmują zarówno biblioteki .NET Core, jak i środowisko uruchomieniowe platformy .NET Core. Począwszy od zestawu .NET Core 2,1 SDK (wersja 2.1.300), samodzielne wdrożenie aplikacji [publikuje najwyższe środowisko uruchomieniowe poprawek na komputerze](https://github.com/dotnet/designs/pull/36). Domyślnie, [`dotnet publish`](../tools/dotnet-publish.md) dla wdrożenia z własnym rozmieszczeniem wybiera najnowszą wersję zainstalowaną jako część zestawu SDK na maszynie publikacji. Dzięki temu wdrożona aplikacja będzie działać z poprawkami zabezpieczeń (i innymi poprawkami) dostępnymi podczas `publish`. Aby można było uzyskać nową poprawkę, należy ponownie opublikować aplikację. Aplikacje samodzielne są tworzone przez określenie `-r <RID>` w `dotnet publish` polecenie lub przez określenie [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) w pliku projektu (csproj/vbproj) lub w wierszu polecenia.

## <a name="patch-version-roll-forward-overview"></a>Omówienie przekazujące wersje poprawek

[`restore`](../tools/dotnet-restore.md), [`build`](../tools/dotnet-build.md) i [`publish`](../tools/dotnet-publish.md) są poleceniami `dotnet`, które mogą być uruchamiane oddzielnie. Wybór środowiska uruchomieniowego jest częścią operacji `restore`, a nie `publish` lub `build`. W przypadku wywołania `publish`zostanie wybrana Najnowsza wersja poprawki. Jeśli wywołasz `publish` z argumentem `--no-restore`, możesz nie uzyskać odpowiedniej wersji poprawki, ponieważ wcześniejsze `restore` mogły nie zostać wykonane przy użyciu nowych zasad publikowania samodzielnych aplikacji. W takim przypadku generowany jest błąd kompilacji z tekstem podobnym do poniższego:

  "Projekt został przywrócony przy użyciu programu Microsoft. servicecore. App w wersji 2.0.0, ale z bieżącymi ustawieniami w zamian zostanie użyta wersja 2.0.6. Aby rozwiązać ten problem, upewnij się, że te same ustawienia są używane do przywracania i dla kolejnych operacji, takich jak Kompilowanie lub publikowanie. Zazwyczaj ten problem może wystąpić, jeśli właściwość RuntimeIdentifier jest ustawiona podczas kompilowania lub publikowania, ale nie podczas przywracania.

> [!NOTE]
> `restore` i `build` mogą być uruchamiane niejawnie jako część innego polecenia, takiego jak `publish`. Gdy program jest uruchamiany niejawnie jako część innego polecenia, są one dostarczane z dodatkowym kontekstem, dzięki czemu tworzone są odpowiednie artefakty. W przypadku `publish` ze środowiskiem uruchomieniowym (na przykład `dotnet publish -r linux-x64`) niejawne `restore` przywraca pakiety dla środowiska uruchomieniowego systemu Linux x64. Jeśli wywołajesz `restore` jawnie, nie przywraca domyślnie pakietów środowiska uruchomieniowego, ponieważ nie ma tego kontekstu.

## <a name="how-to-avoid-restore-during-publish"></a>Jak uniknąć przywracania podczas publikowania

Uruchamianie `restore` w ramach operacji `publish` może być niepożądane dla Twojego scenariusza. Aby uniknąć `restore` `publish` podczas tworzenia aplikacji samodzielnych, należy wykonać następujące czynności:

- Ustaw właściwość `RuntimeIdentifiers` na listę oddzielonych średnikami wszystkich [identyfikatorów RID](../rid-catalog.md) do opublikowania.
- Ustaw `TargetLatestRuntimePatch` właściwość `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Nie przywracaj argumentu z opcjami dotnet publish

Jeśli chcesz utworzyć zarówno aplikacje samodzielne, jak i [aplikacje zależne od platformy](index.md) , przy użyciu tego samego pliku projektu, i chcesz użyć argumentu `--no-restore` z `dotnet publish`, wybierz jedną z następujących wartości:

1. Preferuj zachowanie zależne od platformy. Jeśli aplikacja jest zależna od struktury, jest to zachowanie domyślne. Jeśli aplikacja jest samodzielna i może użyć nie2.1.0ego lokalnego środowiska uruchomieniowego, ustaw `TargetLatestRuntimePatch` na `false` w pliku projektu.

2. Preferuj zachowanie samodzielne. Jeśli aplikacja jest samodzielna, jest to zachowanie domyślne. Jeśli aplikacja jest zależna od struktury i wymaga zainstalowanej najnowszej poprawki, ustaw `TargetLatestRuntimePatch` na `true` w pliku projektu.

3. Przejęcie jawnej kontroli wersji struktury środowiska uruchomieniowego przez ustawienie `RuntimeFrameworkVersion` do określonej wersji poprawki w pliku projektu.
