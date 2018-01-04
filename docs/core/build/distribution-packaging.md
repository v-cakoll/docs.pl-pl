---
title: OPAKOWYWANIE dystrybucji .NET core
description: "Dowiedz się, jak pakietu, nazwę i wersję platformy .NET Core do dystrybucji."
keywords: "Źródło .NET i .NET core, kompilacji"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 71b9d722-c5a8-4271-9ce1-d87e7ae2494d
ms.workload: dotnetcore
ms.openlocfilehash: 9f5cd2f7c4fec553dfdfaf1765663b6896b3061d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-distribution-packaging"></a>OPAKOWYWANIE dystrybucji .NET core

W miarę wprowadzania na coraz więcej platformy .NET Core jest przydatne informacje na temat pakietu, nazwę i wersję go. W ten sposób maintainers pakietu pomoże zapewnić spójne środowisko niezależnie od tego, w której użytkownicy muszą wybrać do uruchomienia .NET.

## <a name="net-core-components"></a>Składniki platformy .NET core

Oprogramowanie .NET core składa się z trzech głównych składników, które muszą być spakowane:

1. **Host** (znanej także jako "muxer") ma dwa różne role: aktywować runtime, aby uruchomić aplikację i Aktywuj zestaw SDK, aby wysłać do niego poleceń. Host jest natywny plik wykonywalny (`dotnet.exe`) i jego towarzyszące bibliotek zasad (zainstalowane w `host/fxr`). Jest ona wbudowana z kodu w [ `dotnet/core-setup` ](https://github.com/dotnet/core-setup/) repozytorium. Brak zwykle tylko jednego hosta na danym komputerze, mimo że, która nie jest ścisłym wymogiem.
2. **Platformę** się środowisko wykonawcze i obsługa bibliotek zarządzanych. Framework może być zainstalowana jako część aplikacji, lub udostępnionego framework w centralnej lokalizacji, które mogą być ponownie używane przez wiele aplikacji. Może być dowolną liczbą udostępnionego struktur zainstalowana na danym komputerze. Struktury udostępnionego na żywo w obszarze `shared/Microsoft.NETCore.App/<version>`. Przetwarza hosta w wersji poprawki. Jeśli odpowiedniej aplikacji `Microsoft.NETCore.App` 1.0.0 i tylko 1.0.4 jest obecny, aplikacja jest uruchamiana przed 1.0.4.
3. **Zestaw SDK** (znanej także jako "narzędzia") to zestaw narzędzi zarządzanych, które mogą służyć do zapisu i tworzenia bibliotek .NET Core i aplikacji. Zestaw SDK zawiera nowe szablony projektu interfejsu wiersza polecenia, MSBuild i zadania kompilacji i obiekty docelowe, NuGet, itp. Użytkownik może mieć wiele zestawów SDK na komputerze (na przykład, aby kompilować projekty jawnie wymagających starsza wersja), ale zaleca się użycie najnowsza wersja narzędzia wydaną.

## <a name="recommended-package-names"></a>Nazwy pakietu zalecane

Nasze zalecenia dla nazwy pakietu są następujące wskazówki. Element utrzymujący pakietu mogą wybrać odchodzenia od niego oparte na różnych powodów, takich jak różnych tradycję dystrybucji określonych w przypadku określania wartości docelowej.

### <a name="minimum-package-set"></a>Ustaw minimalną pakietu

* `dotnet-runtime-[major].[minor]`: udostępnionego framework o określonej wersji (tylko najnowszą wersję poprawki dla danej głównych + pomocnicza kombinacji powinny być dostępne w Menedżera pakietów). **zależności**:`dotnet-host`
* `dotnet-sdk`: najnowszej wersji zestawu SDK. **zależności**: r `dotnet-sdk-[major].[minor]`.
* `dotnet-sdk-[major].[minor]`: zestaw SDK o określonej wersji. Określona wersja jest najwyższej wersji dołączone dołączone struktur udostępnionych, tak, aby użytkownicy można łatwo dotyczą zestawu SDK udostępnionego framework. **zależności**: `dotnet-host`, co najmniej jeden `dotnet-runtime-[major].[minor]` (jedna z środowisk uruchomieniowych jest używana przez zestaw SDK kodu, inne są tutaj dla użytkowników skompilować i uruchomić przed).
* `dotnet-host`: najnowsze hosta.

#### <a name="preview-versions"></a>Wersji Preview

Maintainers pakietu może zadecydować o obejmują wersje Podgląd udostępnionego framework i zestawu SDK. Te nigdy nie powinien być uwzględniany w niewersjonowanych `dotnet-sdk` pakietu, ale może być zwolnione jako numerów wersji pakietów ze znacznikiem Podgląd dodatkowe dołączone do wersji głównej i pomocniczej części nazwy. Na przykład mogą istnieć `dotnet-sdk-2.0-preview-final` pakietu.

### <a name="optional-additional-packages"></a>Opcjonalne dodatkowe pakiety

Niektóre maintainers może wybrać zapewnienie dodatkowych pakietów, takich jak:

* `dotnet-lts`: najnowszą wersję framework udostępnionego długoterminowe pomocy technicznej (LTS). [LTS i bieżącej wersji pociągu](~/docs/core/versions/lts-current.md) odpowiadają cadences inny, na których pobiera zwolniony .NET Core. Użytkownicy mają wybór przyjęcia co najmniej innych pociągu, jak często są one gotowość do aktualizacji w oparciu. To pojęcie jest także powiązany obsługę poziomów, więc może lub nie może być uzasadniona w zależności od distro były uznawane za.

## <a name="disk-layout"></a>Układ dysku

Podczas instalowania pakietów platformy .NET Core, znaczenia względne położenie ich miejsca docelowego docelowe na dysku.
`dotnet.exe` Hosta, które mają zostać umieszczone obok `sdk` i `shared` foldery, które zawierają zawartość wersji `dotnet-sdk` pakietów SDK i `dotnet-runtime` udostępnionego framework pakietów.

Układ dysku, plików i katalogów wewnątrz pakietów jest kontrolą wersji. Oznacza to, że aktualizowanie do najnowszej wersji `dotnet-runtime` instaluje nową wersję obok siebie w poprzednich wersjach, zmniejszenie możliwości fundamentalne istniejących aplikacji przez aktualizację pakietu. Pakiet aktualizacji nie należy usunąć poprzednie wersje.

## <a name="update-policies"></a>Aktualizowanie zasad

Gdy `update` jest wykonywana, zachowanie każdy pakiet jest następujący:

* `dotnet-runtime-[major].[minor]`: nowe wersje poprawki pakietu, ale nowe wersje pomocnicze lub główne są osobne pakiety.
* `dotnet-sdk`: `update` przedstawia głównych do przodu, pomocnicze i wersji poprawki.
* `dotnet-sdk-[major].[minor]`: nowe wersje poprawki pakietu, ale nowe wersje pomocnicze lub główne są osobne pakiety.
* `dotnet-lts`: `update` przedstawia głównych do przodu, pomocnicze i wersji poprawki.

W tym temacie przedstawił Nasze zalecenia dotyczące pakowania .NET Core, jednak każdy distro jest swobodę wersji oferowanie i kiedy. Na przykład distro więcej niż jest aktualne stabilności wartości mogą wybrać tylko wersje przyciągania pomocą train wersji LTS.