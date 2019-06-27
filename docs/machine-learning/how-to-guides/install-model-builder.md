---
title: Jak zainstalować konstruktora modeli
description: Dowiedz się, jak zainstalować narzędzie konstruktora Model w strukturze ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410651"
---
# <a name="how-to-install-mlnet-model-builder"></a>Jak zainstalować konstruktora Model w strukturze ML.NET

Dowiedz się, jak zainstalować strukturze ML.NET konstruktora modelu można dodać usługi machine learning do aplikacji .NET.

> [!NOTE]
> Konstruktor modelu jest obecnie w wersji zapoznawczej.

## <a name="pre-requisites"></a>Wymagania wstępne

- Visual Studio 2017 15.9.12 lub nowszej / Visual Studio 2019 r
- .NET core 2.1 lub nowszej zestawu SDK

## <a name="limitations"></a>Ograniczenia

- Rozszerzenia konstruktora modelu strukturze ML.NET obecnie działa tylko w programie Visual Studio na Windows.
- Szkolenie zestaw danych limitu 1 GB
- Program SQL Server ma limit równy 100 tysięcy wierszy szkolenia
- Microsoft SQL Server Data Tools dla programu Visual Studio 2017 nie jest obsługiwane.

## <a name="install"></a>Zainstaluj

Konstruktor modelu strukturze ML.NET można zainstalować za pośrednictwem witryny Marketplace programu Visual Studio lub z poziomu programu Visual Studio. 

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Pobieranie z [witryny Marketplace programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Postępuj zgodnie z monitami, aby zainstalować na odpowiedniej wersji programu Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**
1. Wewnątrz *rozszerzenia i aktualizacje* monit, wybierz opcję *Online* węzła.
1. Na pasku wyszukiwania, wyszukaj *konstruktora Model w strukturze ML.NET* z wyników, wybierz strukturze ML.NET konstruktora modeli (wersja zapoznawcza)
1. Postępuj zgodnie z monitami, aby ukończyć instalację

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na pasku menu wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**
1. Wewnątrz *rozszerzenia i aktualizacje* monit, wybierz opcję *Online* węzła.
1. Typ *konstruktora Model w strukturze ML.NET* na pasku wyszukiwania wybierz strukturze ML.NET konstruktora modeli (wersja zapoznawcza)
1. Postępuj zgodnie z monitami, aby ukończyć instalację

## <a name="uninstall"></a>Odinstaluj

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**
1. Wewnątrz *rozszerzenia i aktualizacje* monit, a następnie rozwiń *zainstalowane* a następnie wybierz węzeł *narzędzia*
1. Wybierz Model strukturze ML.NET — Konstruktor (wersja zapoznawcza) z listy narzędzi, a następnie wybierz *dezinstalacji*
1. Postępuj zgodnie z monitami, aby ukończyć dezinstalację.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na pasku menu wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**
1. Wewnątrz *rozszerzenia i aktualizacje* monit, a następnie rozwiń *zainstalowane* a następnie wybierz węzeł *narzędzia*
1. Wybierz Model strukturze ML.NET — Konstruktor (wersja zapoznawcza) z listy narzędzi, a następnie wybierz *dezinstalacji*
1. Postępuj zgodnie z monitami, aby ukończyć dezinstalację.

## <a name="upgrade"></a>Uaktualnienie

Proces uaktualniania jest podobny do procesu instalacji. Pobierz najnowszą wersję programu Visual Studio Marketplace albo użyj Menedżera rozszerzeń w programie Visual Studio.
