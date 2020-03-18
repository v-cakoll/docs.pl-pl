---
title: Jak zainstalować Model Konstruktora
description: Dowiedz się, jak zainstalować narzędzie ML.NET Model Builder
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848655"
---
# <a name="how-to-install-mlnet-model-builder"></a>Jak zainstalować ML.NET Model Builder

Dowiedz się, jak zainstalować ML.NET Model Builder, aby dodać uczenie maszynowe do aplikacji .NET.

> [!NOTE]
> Konstruktor modeli jest obecnie w wersji zapoznawczej.

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 w wersji 15.9.12 lub nowszej / Visual Studio 2019
- SDK .NET Core 2.1 lub nowszy.

> [!NOTE]
> Zestaw SDK .NET Core 3.0 nie jest obecnie obsługiwany.

## <a name="limitations"></a>Ograniczenia

- ML.NET Rozszerzenie Konstruktora modeli działa obecnie tylko w programie Visual Studio w systemie Windows.
- Limit zestawu danych szkoleniowych 1 GB
- PROGRAM SQL Server ma limit 100 tysięcy wierszy na szkolenia
- Narzędzia danych programu Microsoft SQL Server dla programu Visual Studio 2017 nie są obsługiwane

## <a name="install"></a>Instalowanie

ML.NET konstruktora modelu można zainstalować za pośrednictwem portalu Visual Studio Marketplace lub z poziomu programu Visual Studio.

### <a name="visual-studio-marketplace"></a>Witryna Visual Studio Marketplace

1. Pobierz z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Postępuj zgodnie z monitami, aby zainstalować odpowiednią wersję programu Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na pasku menu wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > 

    ![Vs2017 otwórz menedżera rozszerzeń okno dialogowe](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online.*
1. Na pasku wyszukiwania wyszukaj *ML.NET Konstruktora modeli* i na podstawie wyników wybierz ML.NET Konstruktora modeli (wersja zapoznawcza)

    ![Vs2017 wyszukiwanie i instalowanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-install-model-builder.png)

1. Postępuj zgodnie z monitami, aby ukończyć instalację

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na pasku menu wybierz pozycję **Rozszerzenia** > **Zarządzaj rozszerzeniami**

    ![Vs2019 otwórz menedżera rozszerzeń okno dialogowe](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* wybierz węzeł *online.*
1. Wpisz *ML.NET Konstruktora modeli* na pasku wyszukiwania wybierz pozycję ML.NET Konstruktor modeli (wersja zapoznawcza)

    ![Vs2019 wyszukiwanie i instalowanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-install-model-builder.png)

1. Postępuj zgodnie z monitami, aby ukończyć instalację

## <a name="uninstall"></a>Dezinstalacja

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na pasku menu wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > 

    ![Vs2017 otwórz zarządzanie rozszerzeniami, okno dialogowe](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *Zainstalowane* i wybierz *pozycję Narzędzia*
1. Wybierz ML.NET Konstruktora modeli (Podgląd) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj*

    ![Vs2017 wyszukiwanie i odinstalowywanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Postępuj zgodnie z instrukcjami, aby zakończyć dezinstalację.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na pasku menu wybierz pozycję **Rozszerzenia** > **Zarządzaj rozszerzeniami**

    ![Vs2019 otwórz zarządzanie rozszerzeniami, okno dialogowe](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. W wierszu *rozszerzenia i aktualizacji* rozwiń węzeł *Zainstalowane* i wybierz *pozycję Narzędzia*
1. Wybierz ML.NET Konstruktora modeli (Podgląd) z listy narzędzi, a następnie wybierz pozycję *Odinstaluj*

    ![Vs2019 wyszukiwanie i odinstalowywanie rozszerzenia Model Builder w oknie dialogowym Menedżera rozszerzeń](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Postępuj zgodnie z instrukcjami, aby zakończyć dezinstalację.

## <a name="upgrade"></a>Uaktualnienie

Proces uaktualniania jest podobny do procesu instalacji. Pobierz najnowszą wersję z programu Visual Studio Marketplace lub użyj Menedżera rozszerzeń w programie Visual Studio.
