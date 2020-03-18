---
title: Przepływ do przodu w czasie wykonywania dla wdrożeń aplikacji .NET Core.
description: Dowiedz się więcej o dotnet publikowania zmian dla wdrożeń samodzielnych.
author: KathleenDollard
ms.date: 05/31/2018
ms.openlocfilehash: 22385c7b5d2bf87755fd51cd6268d21fe3431c74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740784"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Przenoszenie do przodu w czasie samodzielnego środowiska uruchomieniowego wdrożenia

Niezależne [wdrożenia aplikacji](index.md) .NET Core obejmują zarówno biblioteki .NET Core, jak i program runtime .NET Core. Począwszy od .NET Core 2.1 SDK (wersja 2.1.300), niezależne wdrożenie aplikacji [publikuje najwyższy czas pracy poprawki na komputerze](https://github.com/dotnet/designs/pull/36). Domyślnie [`dotnet publish`](../tools/dotnet-publish.md) dla samodzielnego wdrożenia wybiera najnowszą wersję zainstalowaną jako część sdk na komputerze wydawniczym. Dzięki temu wdrożona aplikacja może działać z poprawkami `publish`zabezpieczeń (i innymi poprawkami) dostępnymi podczas . Aplikacja musi zostać ponownie opublikowana w celu uzyskania nowej poprawki. Niezależne aplikacje są tworzone przez `-r <RID>` określenie `dotnet publish` polecenia lub przez określenie [identyfikatora czasu wykonywania (RID)](../rid-catalog.md) w pliku projektu (csproj / vbproj) lub w wierszu polecenia.

## <a name="patch-version-roll-forward-overview"></a>Omówienie przewijania wersji poprawek

[`restore`](../tools/dotnet-restore.md)i [`build`](../tools/dotnet-build.md) [`publish`](../tools/dotnet-publish.md) są `dotnet` poleceniami, które mogą być uruchamiane oddzielnie. Wybór czasu wykonywania jest `restore` częścią `publish` operacji, nie lub `build`. Jeśli zadzwonisz, `publish`zostanie wybrana najnowsza wersja poprawki. Jeśli `publish` wywołasz `--no-restore` z argumentem, a następnie może nie `restore` uzyskać żądaną wersję poprawki, ponieważ wcześniej może nie zostały wykonane z nowych zasad publikowania aplikacji niezależne. W takim przypadku błąd kompilacji jest generowany z tekstem podobnym do następującego:

  "Projekt został przywrócony przy użyciu wersji Microsoft.NETCore.App 2.0.0, ale przy bieżących ustawieniach zostanie użyta wersja 2.0.6. Aby rozwiązać ten problem, upewnij się, że te same ustawienia są używane do przywracania i kolejnych operacji, takich jak kompilacja lub publikowanie. Zazwyczaj ten problem może wystąpić, jeśli Właściwość RuntimeIdentifier jest ustawiona podczas kompilacji lub publikowania, ale nie podczas przywracania."

> [!NOTE]
> `restore`i `build` mogą być uruchamiane niejawnie `publish`jako część innego polecenia, takiego jak . Po uruchomieniu niejawnie jako część innego polecenia, są one dostarczane z dodatkowym kontekstem, dzięki czemu odpowiednie artefakty są produkowane. Podczas `publish` wykonywania (na `dotnet publish -r linux-x64`przykład), niejawne `restore` przywraca pakiety dla uruchomienia linux-x64. Jeśli wywołasz `restore` jawnie, nie przywraca pakietów w czasie wykonywania domyślnie, ponieważ nie ma tego kontekstu.

## <a name="how-to-avoid-restore-during-publish"></a>Jak uniknąć przywracania podczas publikowania

Uruchamianie `restore` w `publish` ramach operacji może być niepożądane dla scenariusza. Aby `restore` uniknąć `publish` podczas tworzenia aplikacji samodzielnych, wykonaj następujące czynności:

- Ustaw `RuntimeIdentifiers` właściwość na listę oddzielone średnikami wszystkich [identyfikatorów IDENTYFIKATORÓW, które](../rid-catalog.md) mają zostać opublikowane.
- Ustaw `TargetLatestRuntimePatch` właściwość `true`na .

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Argument no-restore z opcjami publikowania dotnet

Jeśli chcesz utworzyć zarówno niezależne aplikacje, jak i [aplikacje zależne od struktury](index.md) z `--no-restore` tym `dotnet publish`samym plikiem projektu i chcesz użyć argumentu z , wybierz jedną z następujących czynności:

1. Preferuj zachowanie zależne od struktury. Jeśli aplikacja jest zależna od struktury, jest to zachowanie domyślne. Jeśli aplikacja jest niezależna i może używać niezałatanego lokalnego czasu uruchomieniowego `TargetLatestRuntimePatch` `false` 2.1.0, ustaw wartość w pliku projektu.

2. Preferuj zachowanie samodzielne. Jeśli aplikacja jest niezależna, jest to zachowanie domyślne. Jeśli aplikacja jest zależna od struktury i wymaga `TargetLatestRuntimePatch` zainstalowanej najnowszej poprawki, ustaw ją `true` w pliku projektu.

3. Przejmij jawną kontrolę `RuntimeFrameworkVersion` nad wersją struktury wykonywania, ustawiając określoną wersję poprawki w pliku projektu.
