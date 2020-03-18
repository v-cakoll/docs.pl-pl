---
title: Załaduj dane szkoleniowe dla konstruktora modeli
description: Dowiedz się, jak załadować dane szkoleniowe z bazy danych programu SQL Server lub pliku do użycia w jednym ze scenariuszy Konstruktora modeli dla ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849162"
---
# <a name="load-training-data-into-model-builder"></a>Załaduj dane szkoleniowe do konstruktora modeli

Dowiedz się, jak załadować zestawy danych szkoleniowych z pliku lub bazy danych programu SQL Server do użycia w jednym ze scenariuszy Konstruktora modeli dla ML.NET. Scenariusze Programu Model Builder mogą używać baz danych programu SQL Server, plików obrazów oraz formatów plików CSV lub TSV jako danych szkoleniowych.

## <a name="training-dataset-limitations-in-model-builder"></a>Ograniczenia zestawu danych szkoleniowych w Konstruktorze modeli

Konstruktor modeli ogranicza ilość i typ danych, których można używać w modelach szkoleniowych:

- Dane programu SQL Server: 100 000 wierszy
- Pliki CSV i TSV: Brak limitu rozmiaru
- Obrazy: tylko PNG i JPG.

## <a name="model-builder-scenarios"></a>Scenariusze konstruktora modeli

Program Model Builder ułatwia tworzenie modeli dla następujących scenariuszy uczenia maszynowego:

- Analiza tonacji (klasyfikacja binarna): Klasyfikowanie danych tekstowych do dwóch kategorii.
- Klasyfikacja problemów (klasyfikacja wieloklasowa): Zaklasyfikowanie danych tekstowych do 3 lub więcej kategorii.
- Przewidywanie cen (regresja): Przewidywanie wartości liczbowej.
- Klasyfikacja obrazów (uczenie głębokie): Kategoryzuj obrazy na podstawie cech.
- Scenariusz niestandardowy: Tworzenie scenariuszy niestandardowych na podstawie danych przy użyciu regresji, klasyfikacji i innych zadań.

W tym artykule omówiono scenariusze klasyfikacji i regresji z danymi tekstowymi lub liczbowymi oraz scenariuszami klasyfikacji obrazów.

## <a name="load-text-or-numeric-data-from-a-file"></a>Ładowanie tekstu lub danych liczbowych z pliku

Do Konstruktora modeli można załadować dane tekstowe lub liczbowe z pliku. Akceptuje formaty plików rozdzielanych przecinkami (CSV) lub rozdzielanych kartami (TSV).

1. W kroku danych Konstruktora modeli wybierz **pozycję Plik** z listy rozwijanej źródła danych.
2. Zaznacz przycisk obok pola **tekstowego Wybierz plik** i użyj Eksploratora plików, aby przeglądać i wybierać plik danych.
3. Wybierz kategorię z listy rozwijanej **Kolumna do przewidzenia (etykieta).**
4. Z listy **rozwijanej Kolumny wejściowe (Funkcje)** upewnij się, że kolumny danych, które chcesz uwzględnić, są zaznaczone.

Gotowe skonfigurowanie pliku źródła danych dla Konstruktora modeli. Wybierz **łącze Pociąg,** aby przejść do następnego kroku w konstruktorze modeli.

## <a name="load-data-from-a-sql-server-database"></a>Ładowanie danych z bazy danych programu SQL Server

Program Model Builder obsługuje ładowanie danych z lokalnych i zdalnych baz danych programu SQL Server.

Aby załadować dane z bazy danych programu SQL Server do konstruktora modułów:

1. W kroku tworzenia danych konstruktora modeli wybierz pozycję **SQL Server** z listy rozwijanej źródła danych.
1. Zaznacz przycisk obok pola tekstowego Połącz z **bazą danych programu SQL Server.**
    1. W oknie dialogowym **Wybieranie danych** wybierz pozycję **Plik bazy danych programu Microsoft SQL Server**.
    1. Wyczyść zaznaczenie pola wyboru **Zawsze używaj tego zaznaczenia** i wybierz **pozycję Kontynuuj**
    1. W oknie dialogowym **Właściwości połączenia** wybierz pozycję **Przeglądaj** i wybierz pobraną opcję . MDF.
    1. Wybierz **OK**
1. Wybierz nazwę zestawu danych z **listy rozwijanej Nazwa tabeli.**
1. Z listy rozwijanej **Kolumna do przewidywania (etykieta)** wybierz kategorię danych, w której chcesz dokonać przewidywania.
1. Z listy **rozwijanej Kolumny wejściowe (Funkcje)** upewnij się, że kolumny, które chcesz uwzględnić, są zaznaczone.

Gotowe skonfigurowanie pliku źródła danych dla Konstruktora modeli. Wybierz **łącze Pociąg,** aby przejść do następnego kroku w konstruktorze modeli.

## <a name="set-up-image-data-files"></a>Konfigurowanie plików danych obrazu

Model Builder oczekuje, że dane obrazu będą plikami JPG lub PNG zorganizowanymi w foldery odpowiadające kategoriom klasyfikacji.

Aby załadować obrazy do Konstruktora modeli, należy podać ścieżkę do jednego katalogu najwyższego poziomu:

- Ten katalog najwyższego poziomu zawiera jeden podfolder dla każdej z kategorii do przewidzenia.
- Każdy podfolder zawiera pliki obrazów należące do jego kategorii.

W strukturze folderów przedstawionej poniżej katalog najwyższego poziomu jest *flower_photos*. Istnieje pięć podkatalogów odpowiadających kategoriom, które chcesz przewidzieć: stokrotki, mniszka lekarskiego, róż, słoneczników i tulipanów. Każdy z tych podkatalogów zawiera obrazy należące do odpowiedniej kategorii.

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

Wykonaj następujące samouczki, aby tworzyć aplikacje do uczenia maszynowego za pomocą programu Model Builder:

- [Przewidywanie cen za pomocą regresji](../tutorials/predict-prices-with-model-builder.md)
- [Analizowanie opinii w aplikacji sieci web przy użyciu klasyfikacji binarnej](../tutorials/sentiment-analysis-model-builder.md )

Jeśli szkolisz model przy użyciu kodu, [dowiedz się, jak załadować dane przy użyciu ML.NET interfejsu API](load-data-ml-net.md).
