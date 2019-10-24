---
title: Jak zainstalować program model Builder
description: Dowiedz się, jak zainstalować narzędzie ML.NET model Builder
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774570"
---
# <a name="how-to-install-mlnet-model-builder"></a>Jak zainstalować program ML.NET model Builder

Dowiedz się, jak zainstalować program ML.NET model Builder, aby dodać Uczenie maszynowe do aplikacji platformy .NET.

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="pre-requisites"></a>Wymagania wstępne

- Visual Studio 2017 w wersji 15.9.12 lub nowszej/Visual Studio 2019
- Zestaw SDK platformy .NET Core 2,1 lub nowszej

## <a name="limitations"></a>Ograniczenia

- Rozszerzenie konstruktora modelu ML.NET aktualnie działa tylko w programie Visual Studio w systemie Windows.
- Limit zestawu danych szkolenia wynoszący 1 GB
- SQL Server ma limit 100 000 wierszy na potrzeby szkolenia
- Narzędzia Microsoft SQL Server Data Tools for Visual Studio 2017 nie są obsługiwane

## <a name="install"></a>Zainstaluj

Konstruktora modelu ML.NET można zainstalować za pośrednictwem Visual Studio Marketplace lub z poziomu programu Visual Studio.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Pobierz z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Postępuj zgodnie z monitami, aby zainstalować odpowiednie wersje programu Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na pasku menu wybierz kolejno opcje **narzędzia**  > **rozszerzenia i aktualizacje** .

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń program VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .
1. Na pasku wyszukiwania Wyszukaj pozycję *ml.NET model Builder* i z wyników wybierz pozycję ml.NET model Builder (wersja zapoznawcza).

    ![Program VS2017 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-install-model-builder.png)

1. Postępuj zgodnie z monitami, aby zakończyć instalację.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na pasku menu wybierz pozycję **rozszerzenia**  > **Zarządzanie rozszerzeniami**

    ![Okno dialogowe Otwieranie Menedżera rozszerzeń VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online* .
1. Wpisz *ml.NET model Builder* na pasku wyszukiwania wybierz pozycję ml.NET model Builder (wersja zapoznawcza)

    ![VS2019 wyszukiwanie i Instalowanie rozszerzenia konstruktora modelu w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-install-model-builder.png)

1. Postępuj zgodnie z monitami, aby zakończyć instalację.

## <a name="uninstall"></a>Odinstaluj

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na pasku menu wybierz kolejno opcje **narzędzia**  > **rozszerzenia i aktualizacje** .

    ![Program VS2017 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*
1. Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .

    ![Rozszerzenie program VS2017 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Postępuj zgodnie z monitami, aby ukończyć dezinstalację.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na pasku menu wybierz pozycję **rozszerzenia**  > **Zarządzanie rozszerzeniami**

    ![VS2019 Otwórz okno dialogowe zarządzania rozszerzeniami](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *zainstalowany* i wybierz pozycję *Narzędzia*
1. Wybierz pozycję ML.NET model Builder (wersja zapoznawcza) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj* .

    ![Rozszerzenie VS2019 wyszukiwanie i odinstalowywanie konstruktora modelu w oknie dialogowym Menedżer rozszerzeń](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Postępuj zgodnie z monitami, aby ukończyć dezinstalację.

## <a name="upgrade"></a>Uaktualniony

Proces uaktualniania jest podobny do procesu instalacji. Pobierz najnowszą wersję z programu Visual Studio Marketplace lub użyj Menedżera rozszerzeń w programie Visual Studio.
