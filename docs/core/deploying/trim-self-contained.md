---
title: Przycinanie samodzielnych aplikacji
description: Dowiedz się, jak przycinać samodzielne aplikacje, aby zmniejszyć ich rozmiar. .NET Core pakiety środowiska wykonawczego z aplikacją, która jest publikowana samodzielnie i zazwyczaj zawiera więcej środowiska wykonawczego, a następnie jest konieczne.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242924"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Przycinanie samodzielnych wdrożeń i plików wykonywalnych

Podczas publikowania aplikacji samodzielny, .NET Core środowiska uruchomieniowego jest powiązany z aplikacją. Ten pakiet dodaje znaczną ilość zawartości do spakowanej aplikacji. Jeśli chodzi o wdrażanie aplikacji, rozmiar jest często ważnym czynnikiem. Utrzymanie rozmiaru aplikacji pakietu tak małe, jak to możliwe jest zazwyczaj celem dla deweloperów aplikacji.

W zależności od złożoności aplikacji do uruchomienia aplikacji wymagany jest tylko podzbiór środowiska wykonawczego. Te nieużywane części środowiska wykonawczego są niepotrzebne i mogą być przycinane z spakowanej aplikacji.

Funkcja przycinania działa przez sprawdzenie plików binarnych aplikacji w celu odnajdywania i tworzenia wykresu wymaganych zestawów środowiska wykonawczego. Pozostałe zestawy środowiska wykonawczego, do których nie istnieją odwołania, są wykluczone.

> [!NOTE]
> Przycinanie jest funkcją eksperymentalną w .NET Core 3.1 i jest dostępne _tylko_ dla aplikacji, które są publikowane samodzielnie.

## <a name="prevent-assemblies-from-being-trimmed"></a>Zapobieganie przycinaniu zespołów

Istnieją scenariusze, w których funkcja przycinania nie będzie wykryć odwołań. Na przykład gdy odbicie jest używany w zestawie środowiska wykonawczego, przez aplikację lub biblioteki, do którego odwołuje się aplikacja, zestaw nie jest bezpośrednio odwołuje. Przycinanie nie jest świadomy tych pośrednich odwołań i wyklucza bibliotekę z opublikowanego folderu.

Gdy kod pośrednio odwołuje się do złożenia za pomocą odbicia, można zapobiec `<TrimmerRootAssembly>` przycinaniu złożenia z ustawieniem. W poniższym przykładzie pokazano, `System.Security` jak zapobiec przycinaniu zestawu o nazwie zestawu:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Przycinanie aplikacji - CLI

Przytnij aplikację za pomocą polecenia [publikowania dotnet.](../tools/dotnet-publish.md) Podczas publikowania aplikacji ustaw następujące trzy ustawienia:

- Publikować jako samodzielne:`--self-contained true`
- Wyłącz publikowanie pojedynczych plików:`-p:PublishSingleFile=false`
- Włącz przycinanie:`p:PublishTrimmed=true`

Poniższy przykład publikuje aplikację dla systemu Windows 10 jako samodzielną i przycina dane wyjściowe.

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core w pliku .NET Core CLI](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Przycinanie aplikacji — Visual Studio

Visual Studio tworzy profile publikowania wielokrotnegoużytnia, które kontrolują sposób publikowania aplikacji.

01. W okienku **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, który chcesz opublikować. Wybierz **pozycję Publikuj...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Eksplorator rozwiązań z menu z zaznaczonym prawym przyciskiem myszy z zaznaczoną opcją Publikuj.":::

    Jeśli nie masz jeszcze profilu publikowania, postępuj zgodnie z instrukcjami, aby go utworzyć i wybrać typ docelowy **folderu.**

01. Wybierz **pozycję Edytuj**.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Profil publikowania w programie Visual Studio za pomocą przycisku edycji.":::

01. W oknie dialogowym **Ustawienia profilu** ustaw następujące opcje:

    - Ustaw **tryb wdrażania** na **samodzielny**.
    - Ustaw **docelowe środowisko uruchomieniowe** na platformie, na której chcesz opublikować.
    - Wybierz **pozycję Przytnij nieużywane złożenia (w podglądzie)**.

    Wybierz **pozycję Zapisz,** aby zapisać ustawienia i powrócić do okna dialogowego **Publikowanie.**

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Okno dialogowe Ustawień profilu z wyróżnionym trybem wdrażania, docelowym środowiskiem uruchomieniowym i przycinaniem nieużywanych zestawów.":::

01. Wybierz **pozycję Publikuj,** aby opublikować przycięcie aplikacji.

Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core w programie Visual Studio](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Przycinanie aplikacji — Visual Studio dla komputerów Mac

Program Visual Studio dla komputerów Mac nie udostępnia opcji przycinania aplikacji podczas publikowania. Musisz opublikować ręcznie, postępując zgodnie z instrukcjami z sekcji [Przytnij aplikację — cli.](#trim-your-app---cli) Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core w pliku .NET Core CLI](deploy-with-cli.md).

## <a name="see-also"></a>Zobacz też

- [Wdrożenie aplikacji .NET Core](index.md).
- [Publikowanie aplikacji .NET Core za pomocą interfejsu wiersza polecenia .NET Core](deploy-with-cli.md).
- [Publikowanie aplikacji .NET Core w programie Visual Studio](deploy-with-vs.md).
- [polecenie publikowania dotnet](../tools/dotnet-publish.md).
