---
title: Dostawcy typów
description: 'Dowiedz się, w jaki sposób dostawca typów języka F # to składnik, który dostarcza typy, właściwości i metody do użycia w programach.'
ms.date: 04/02/2018
ms.openlocfilehash: eae64d2e318ee93f0b8d5b91f0c6da6c91743527
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202113"
---
# <a name="type-providers"></a>Dostawcy typów

Dostawca typów języka F# to składnik, który dostarcza typy, właściwości i metody używane w programie. Dostawcy typów generują elementy znane jako **dostarczone typy**, które są generowane przez kompilator F # i są oparte na zewnętrznym źródle danych.

Na przykład dostawca typów języka F # dla programu SQL Server może generować typy reprezentujące tabele i kolumny w relacyjnej bazie danych. W rzeczywistości jest to typ dostawcy typu [SqlProvider](https://fsprojects.github.io/SQLProvider/) .

Dostarczone typy są zależne od parametrów wejściowych dostawcy typów. Takie dane wejściowe mogą być przykładowym źródłem danych (takim jak plik schematu JSON), adres URL wskazujący bezpośrednio na usługę zewnętrzną lub parametry połączenia ze źródłem danych. Dostawca typów może również upewnić się, że grupy typów są rozwinięte na żądanie. oznacza to, że są one rozwinięte, jeśli do tych typów rzeczywiście odwołuje się program. Umożliwia to bezpośrednią integrację na żądanie przestrzeni informacji o wielkiej skali, takich jak sieciowe rynki danych, w sposób silnie typizowany.

## <a name="generative-and-erased-type-providers"></a>Dostawcy typów odzyskania i wymazanych

Dostawcy typów mają dwie formy: dostępne do odzyskania i wymazywania.

Dostawcy typów pozyskania tworzą typy, które mogą być zapisywane jako typy .NET w zestawie, w którym są produkowane. Dzięki temu mogą one być używane z kodu w innych zestawach. Oznacza to, że reprezentacja źródła danych musi być na ogół taka, która jest możliwe do reprezentowania z typami .NET.

Wymazywanie dostawców typów produkuje typy, które mogą być używane tylko w zestawie lub projekcie, z których są generowane. Typy są tymczasowe; oznacza to, że nie są one zapisywane w zestawie i nie mogą być używane przez kod w innych zestawach. Mogą zawierać *opóźnione* składowe, co pozwala na korzystanie z dostarczonych typów z potencjalnie nieskończonej przestrzeni informacji. Są one przydatne do korzystania z małego podzestawu dużych i połączonych źródeł danych.

## <a name="commonly-used-type-providers"></a>Najczęściej używane dostawcy typów

Następujące powszechnie używane biblioteki zawierają dostawców typów do różnych celów:

- [FSharp. Data](https://fsharp.github.io/FSharp.Data/) zawiera dostawców typów dla formatów dokumentów JSON, XML, CSV i HTML oraz zasobów.
- Program [Sqldostarczający](https://fsprojects.github.io/SQLProvider/) zapewnia silnie określony dostęp do relacji baz danych za poorednictwem mapowania obiektów i zapytań języka F # LINQ względem tych źródeł danych.
- [FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) ma zestaw dostawców typów dla zaznaczonego osadzania języka T-SQL w języku F #.
- [Dostawca typów usługi Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/) udostępnia typy dla obiektów blob, tabel i kolejek platformy Azure, dzięki czemu można uzyskiwać dostęp do tych zasobów bez konieczności określania nazw zasobów jako ciągów w całym programie.
- [FSharp. Data. GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) zawiera **GraphQLProvider**, który dostarcza typy oparte na serwerze GraphQL określonym za pomocą adresu URL.

W razie potrzeby można [utworzyć własnych niestandardowych dostawców typów](creating-a-type-provider.md)lub dostawców typów referencyjnych, które zostały utworzone przez inne osoby. Na przykład organizacja ma usługę danych dostarczającą dużą i rosnącą liczbę nazwanych zestawów danych, z których każdy ma własny stabilny schemat danych. Można utworzyć dostawcę typów, który odczytuje te schematy i przedstawia programiście najnowsze dostępne zestawy danych w sposób mocno typizowany.

## <a name="see-also"></a>Zobacz także

- [Samouczek: Tworzenie dostawcy typów](creating-a-type-provider.md)
- [Dokumentacja języka F #](../../language-reference/index.md)
