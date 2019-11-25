---
title: Ładowanie danych szkoleniowych dla konstruktora modelu
description: Dowiedz się, jak ładować dane szkoleniowe z bazy danych SQL Server lub pliku do użycia w jednym z scenariuszy konstruktora modelu dla ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: cc93b3f77284ed283a8d7cbd52b8cd02b4fd9066
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977051"
---
# <a name="load-training-data-into-model-builder"></a>Ładowanie danych szkoleniowych do konstruktora modelu

Dowiedz się, jak ładować zbiory danych szkoleniowych z pliku lub SQL Serverj do użycia w jednym z scenariuszy konstruktora modelu dla ML.NET. Scenariusze konstruktora modeli mogą używać SQL Server baz danych, plików obrazów oraz formatów plików CSV lub TSV jako danych szkoleniowych.

## <a name="training-dataset-limitations-in-model-builder"></a>Ograniczenia szkolenia zestawu danych w konstruktorze modelu

Konstruktor modelu ogranicza ilość i typ danych, których można użyć do modeli szkoleń:

- SQL Server dane: 100 000 wierszy
- Pliki CSV i TSV: bez limitu rozmiaru
- Obrazy: tylko PNG i JPG.

## <a name="model-builder-scenarios"></a>Scenariusze konstruktora modelu

Konstruktor modeli ułatwia tworzenie modeli dla następujących scenariuszy uczenia maszynowego:

- Analiza tonacji (klasyfikacja binarna): klasyfikowanie danych tekstowych do dwóch kategorii.
- Klasyfikacja problemu (Klasyfikacja wieloklasowa): klasyfikowanie danych tekstowych w 3 lub większej liczbie kategorii.
- Prognoza cen (regresja): przewidywanie wartości liczbowej.
- Klasyfikacja obrazu (głębokie uczenie): klasyfikowanie obrazów na podstawie właściwości.
- Scenariusz niestandardowy: Tworzenie niestandardowych scenariuszy na podstawie danych przy użyciu regresji, klasyfikacji i innych zadań.

W tym artykule omówiono scenariusze klasyfikacji i regresji z danymi tekstowymi lub liczbowymi oraz scenariusze klasyfikacji obrazów.

## <a name="load-text-or-numeric-data-from-a-file"></a>Załaduj dane tekstowe lub liczbowe z pliku

Możesz załadować dane tekstowe lub liczbowe z pliku do konstruktora modelu. Akceptowane są formaty plików rozdzielane przecinkami (CSV) lub rozdzielane znakami tabulacji (TSV).

1. W kroku dane konstruktora modelu wybierz pozycję **plik** z listy rozwijanej Źródło danych.
2. Wybierz przycisk obok pola tekstowego **Wybierz plik** , a następnie użyj Eksploratora plików, aby przeglądać i wybrać plik danych.
3. Wybierz kategorię w **kolumnie do przewidywania (etykieta)** listy rozwijanej.
4. Z listy rozwijanej **kolumny wejściowe (funkcje)** upewnij się, że są zaznaczone kolumny danych, które chcesz dołączyć.

Wszystko gotowe do skonfigurowania pliku źródła danych dla konstruktora modelu. Wybierz łącze **uczenie** , aby przejść do następnego kroku w programie model Builder.

## <a name="load-data-from-a-sql-server-database"></a>Ładowanie danych z bazy danych SQL Server

Konstruktor modelu obsługuje ładowanie danych z lokalnych i zdalnych baz danych SQL Server.

Aby załadować dane z bazy danych SQL Server do konstruktora modułów:

1. W kroku dane konstruktora modelu wybierz z listy rozwijanej Źródło danych pozycję **SQL Server** .
1. Zaznacz przycisk obok pola tekstowego **Połącz z bazą danych SQL Server** .
    1. W oknie dialogowym **Wybierz dane** wybierz pozycję **plik bazy danych Microsoft SQL Server**.
    1. Usuń zaznaczenie pola wyboru **zawsze używaj tego zaznaczenia** i wybierz pozycję **Kontynuuj** .
    1. W oknie dialogowym **Właściwości połączenia** wybierz pozycję **Przeglądaj** i wybierz pobrane. Plik MDF.
    1. Wybierz **przycisk OK**
1. Wybierz nazwę zestawu danych z listy rozwijanej **Nazwa tabeli** .
1. Z listy rozwijanej **kolumna do prognozowania (etykieta)** wybierz kategorię danych, dla której chcesz dokonać przewidywania.
1. Z listy rozwijanej **kolumny wejściowe (funkcje)** upewnij się, że kolumny, które chcesz dołączyć, są zaznaczone.

Wszystko gotowe do skonfigurowania pliku źródła danych dla konstruktora modelu. Wybierz łącze **uczenie** , aby przejść do następnego kroku w programie model Builder.

## <a name="set-up-image-data-files"></a>Konfigurowanie plików danych obrazu

Konstruktor modelu oczekuje, że dane obrazu mają być pliki JPG lub PNG zorganizowane w folderach, które odpowiadają kategoriom klasyfikacji.

Aby załadować obrazy do konstruktora modelu, podaj ścieżkę do jednego katalogu najwyższego poziomu:

- Ten katalog najwyższego poziomu zawiera jeden podfolder dla każdej z kategorii do przewidywania.
- Każdy podfolder zawiera pliki obrazów należące do tej kategorii.

W strukturze folderów zilustrowanej poniżej katalog najwyższego poziomu jest *flower_photos*. Istnieje pięć podkatalogów odpowiadających kategoriom, które mają zostać przewidywalne: łańcuchy, Dandelion, róże, przepływy i Tulips. Każdy z tych podkatalogów zawiera obrazy należące do odpowiedniej kategorii.

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a>Następne kroki

Postępuj zgodnie z tymi samouczkami, aby tworzyć aplikacje uczenia maszynowego za pomocą konstruktora modeli:

- [Przewidywanie cen przy użyciu regresji](../tutorials/predict-prices-with-model-builder.md)
- [Analizowanie tonacji w aplikacji sieci Web przy użyciu klasyfikacji binarnej](../tutorials/sentiment-analysis-model-builder.md )

Jeśli przekazujesz model przy użyciu kodu, [Dowiedz się, jak ładować dane przy użyciu interfejsu API ml.NET](load-data-ml-net.md).
