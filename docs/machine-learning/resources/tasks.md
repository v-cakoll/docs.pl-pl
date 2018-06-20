---
title: Machine learning zadania
description: Poznaj inną maszynę uczenia zadań obsługiwanych w ML.NET.
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 875006a9cddb87b5f9436b78773420858fd842dd
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208317"
---
# <a name="machine-learning-tasks"></a>Machine learning zadania

Podczas tworzenia modelu uczenia maszynowego, należy najpierw zdefiniować, co to są zostaje do osiągnięcia z danymi. Po można wybrać maszynie prawo uczenia zadań w danej sytuacji. Poniższa lista zawiera inną maszynę uczenia zadań, które są dostępne, a niektóre typowe przypadki użycia. 

> [!NOTE]
> ML.NET jest obecnie w przeglądzie. Nie wszystkie machine learning zadania są obecnie obsługiwane. Aby przesłać żądanie niektórych zadań, należy otworzyć problemu w [repozytorium dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues).

> [!NOTE]
> ML.NET nie obsługuje obecnie zadania uczenia maszyny z obrazami. Obsługa zostanie dodana w przyszłych wersjach. 

## <a name="binary-classification"></a>klasyfikacji binarnej

A [nadzorowanego uczenia maszynowego](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania, którego wystąpienia danych należy do dwóch klas (kategorie). Algorytm klasyfikacji danych wejściowych to zestaw przykładów etykietą, gdzie każda etykieta jest liczbą całkowitą, 0 lub 1. Dane wyjściowe algorytm klasyfikacji binarnej jest klasyfikatora, która służy do prognozowania klasy nowe wystąpienia bez etykiety. Przykładowe scenariusze klasyfikacji binarnej obejmują:

* [Opis wskaźniki nastrojów klientów komentarzy Twitter](../tutorials/sentiment-analysis.md) jako "dodatnią" lub "ujemną".
* Diagnozowanie czy pacjenta ma pewnej choroby, czy nie.
* Podjęciem decyzji o oznaczyć wiadomości e-mail jako "spamu" lub nie.

Aby uzyskać więcej informacji, zobacz [klasyfikacji binarnej](https://en.wikipedia.org/wiki/Binary_classification) artykuł w witrynie Wikipedia.

## <a name="multiclass-classification"></a>wieloklasowej klasyfikacji

A [nadzorowanego uczenia maszynowego](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania klasy (kategoria) wystąpienia danych. Algorytm klasyfikacji danych wejściowych jest zbiorem etykietą przykłady. Każda etykieta jest liczbą całkowitą od 0 do k-1, gdzie k liczby klas. Dane wyjściowe algorytm klasyfikacji jest klasyfikatora, która służy do prognozowania klasy nowe wystąpienia bez etykiety. Przykłady scenariuszy wielu klas klasyfikacji:

* Określanie rodzaj dog jako "Siberian Husky", "Złotego odbiorcy", "Poodle",... itd.
* Opis filmu przegląda jako "dodatnią", "neutralne" lub "ujemną".
* Przegląda kategoryzowania hoteli jako "Lokalizacja", "price", "czystości" itp.

Aby uzyskać więcej informacji, zobacz [Wieloklasowej klasyfikacji](https://en.wikipedia.org/wiki/Multiclass_classification) artykuł w witrynie Wikipedia.

## <a name="regression"></a>Regresja

A [nadzorowanego uczenia maszynowego](glossary.md#supervised-machine-learning) zadanie, które służy do prognozowania wartość etykiety z zestawu powiązanych funkcji. Etykiety można rzeczywistych wartości, a nie z ograniczoną liczbą permutacji zestaw wartości, tak jak zadań klasyfikacji. Model regresji algorytmów zależności etykiety na jego powiązanych funkcji, aby określić sposób zmieni etykiety jako wartości funkcji są różne. Dane wejściowe algorytm regresji to zestaw przykładów z etykietami znane wartości. Dane wyjściowe algorytm regresji jest funkcję, która służy do prognozowania wartości etykiety dla dowolnego nowego zestawu wejściowego funkcji. Przykładowe scenariusze regresji obejmują:

* Prognozowanie cen dom na podstawie atrybutów dom, takie jak Liczba sypialni, lokalizacji lub rozmiaru.
* Przewidywania przyszłych giełdowych na podstawie danych historycznych i trendów rynku bieżącej.
* Prognozowanie sprzedaży produktu oparte na anonsowanie budżetu.

> [!NOTE]
> Obecnie ML.NET nadal jest kompilowany obsługę zadań regresji, które obejmują szeregów czasowych.

## <a name="clustering"></a>Klaster

[Nienadzorowane uczenia maszynowego](glossary.md#unsupervised-machine-learning) zadanie, które służy do grupy wystąpień danych w klastrach zawierających podobne charakterystyki. Klastra może także służyć do identyfikowania relacje w zestawie danych, która nie może być logicznie pochodzi przez obserwacji przeglądania lub prosty. Wejściami i wyjściami klastrowania algorytmu zależy od metody wybrany. Można wykonać dystrybucji, centroidę wzdłuż, łączności lub opartego na gęstości. ML.NET obsługuje obecnie centroidę wzdłuż opartego na używanie K-średnich klastra. Scenariusze z klastrowaniem należą:

* Opis segmentów hoteli gości na podstawie zwyczaje i właściwości opcji hoteli.
* Identyfikowanie segmentów klientów i demograficznych ułatwiająca tworzenie kampanii reklamowych docelowych.
* Kategoryzowania spisu w oparciu metryki produkcyjny.

## <a name="anomaly-detection-coming-soon"></a>Wykrywanie anomalii (*wkrótce*)

## <a name="ranking-coming-soon"></a>Klasyfikacja (*wkrótce*)

## <a name="recommendation-coming-soon"></a>Zalecenie (*wkrótce*)

