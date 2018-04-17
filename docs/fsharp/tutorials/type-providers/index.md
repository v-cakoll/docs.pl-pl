---
title: Dostawcy typów
description: 'Dowiedz się, jak dostawcy typów F # jest składnikiem, który zawiera typy, właściwości i metod do użycia w programach.'
author: cartermp
ms.author: phcart
ms.date: 04/02/2018
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
ms.openlocfilehash: 248fb2db2364cdad53e701603fd2cada33498701
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="type-providers"></a>Dostawcy typów

Dostawca typów języka F# to składnik, który dostarcza typy, właściwości i metody używane w programie. Generowanie dostawcy typów tak zwane **podane typy**, które są generowane przez kompilator języka F # i są oparte na zewnętrznym źródłem danych.

Na przykład F # typ dostawcy dla serwera SQL może wygenerować typy reprezentujące tabel i kolumn w relacyjnej bazie danych. W rzeczywistości, co jest [SQLProvider](https://fsprojects.github.io/SQLProvider/) jest typ dostawcy.

Pod warunkiem, że typy są zależne od dostawcy typów parametry wejściowe. Takie dane wejściowe mogą być źródłem danych przykładowych (na przykład plik schematu JSON) adres URL wskazuje bezpośrednio do zewnętrznej usługi lub parametry połączenia ze źródłem danych. Typ dostawcy można również upewnij się, że grupy typy są tylko rozszerzone na żądanie; oznacza to, że ich rozwinięciu Jeśli typy faktycznie przywoływane przez program. Umożliwia to bezpośrednią integrację na żądanie przestrzeni informacji o wielkiej skali, takich jak sieciowe rynki danych, w sposób silnie typizowany.

## <a name="generative-and-erased-type-providers"></a>Dostawcy typów generative i Wymazanej

Dostawcy typów są dostępne w dwóch formach: Generative i Wymazanej.

Dostawcy typów generative tworzy typy, które mogą być zapisywane jako typów .NET do zestawu, w którym są produkowane. Umożliwia im to być używane z kodu w innych zestawów. Oznacza to, że reprezentacja typu źródła danych zwykle musi być taki, który jest możliwe do reprezentowania z typów .NET.

Wymazywanie dostawców typów tworzy typy, które mogą być używane tylko w zestawie lub projektu, które są generowane na podstawie. Typy tymczasowych; oznacza to, że nie są zapisywane w zestawie i nie mogą być używane przez kod w innych zestawów. Mogą one zawierać *opóźnione* członków, co umożliwia użycie podane typy z obszaru potencjalnie nieskończone informacji. Są one używane przy użyciu małego podzbioru źródłem duży i połączonych danych.

## <a name="commonly-used-type-providers"></a>Najczęściej używanych dostawców typów

Następujące biblioteki powszechnie używane zawiera typ dostawcy do różnych celów:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) zawiera dostawców typów JSON, XML, CSV i HTML dokumentów formaty i zasobów.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) udostępnia silnie typizowane dostępu do baz danych relacji przy użyciu mapowania obiektu i F # LINQ zapytań dotyczących tych źródeł danych.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) zestaw dostawców typów dla kompilacji sprawdził osadzania T-SQL w języku F #.
- [Dostawca usługi Azure typ magazynu](https://fsprojects.github.io/AzureStorageTypeProvider/) zapewnia typy do obiektów blob Azure, tabel i kolejek, co umożliwia dostęp do tych zasobów, bez konieczności określ nazwy zasobu jako ciągi w programie.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) zawiera **GraphQLProvider**, który zawiera typy oparte na serwerze GraphQL określony przez adres URL.

W przypadku, gdy to konieczne, możesz [tworzenie własnych dostawców niestandardowych typów](creating-a-type-provider.md), lub odwołać dostawców typów, które zostały utworzone przez innych użytkowników. Na przykład organizacja ma usługę danych dostarczającą dużą i rosnącą liczbę nazwanych zestawów danych, z których każdy ma własny stabilny schemat danych. Można utworzyć dostawcę typów, który odczytuje te schematy i przedstawia programiście najnowsze dostępne zestawy danych w sposób mocno typizowany.

## <a name="see-also"></a>Zobacz też
[Samouczek: Tworzenie dostawcy typów](creating-a-type-provider.md)

[Dokumentacja języka F#](../../language-reference/index.md)

[Visual F#](../../index.md)
