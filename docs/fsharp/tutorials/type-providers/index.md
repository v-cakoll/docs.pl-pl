---
title: Dostawcy typów
description: Dowiedz się, jak dostawca typów języka F# to składnik, który zawiera typy, właściwości i metody używane w programach.
ms.date: 04/02/2018
ms.openlocfilehash: 5fa9de229caa2ec3ba4a248ca5cd1c8aa5adb230
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "46697766"
---
# <a name="type-providers"></a>Dostawcy typów

Dostawca typów języka F# to składnik, który dostarcza typy, właściwości i metody używane w programie. Generowanie dostawców typów, co to są znane jako **podane typy**, które są generowane przez kompilator F# i opierają się na zewnętrznego źródła danych.

Na przykład dostawcę typów F# do języka SQL, można wygenerować typy reprezentujące tabele i kolumny w relacyjnej bazie danych. W rzeczywistości, co jest [SQLProvider](https://fsprojects.github.io/SQLProvider/) jest dostawcy typów.

Pod warunkiem, że typy są zależne od parametrów wejściowych do dostawcy typu. Takie dane wejściowe mogą być przykładowe źródło danych (na przykład plik schematu JSON) adres URL wskazujący bezpośrednio do usługi zewnętrznej lub parametry połączenia ze źródłem danych. Dostawca typów może również zagwarantować, że grupy typów są tylko rozszerzone na żądanie; oznacza to, że one rozszerzane, jeśli typy odwołuje się program. Umożliwia to bezpośrednią integrację na żądanie przestrzeni informacji o wielkiej skali, takich jak sieciowe rynki danych, w sposób silnie typizowany.

## <a name="generative-and-erased-type-providers"></a>Dostawcy typów generatywną i wymazane

Dostawcy typów są dostępne w dwóch formach: Generatywną i wymazane.

Generatywną dostawców typów generuje typy, które mogą być zapisywane jako typów .NET do zestawu, w którym są tworzone. Uprawnienie pozwoli im do użycia z kodu w innych zestawach. Oznacza to, że wpisane reprezentujący źródło danych zazwyczaj musi być taki, który jest możliwe do reprezentowania z typami .NET.

Wymazywanie dostawców typów generuje typy, które mogą być używane tylko w zestawie lub projektu, które są generowane na podstawie. Typy są efemeryczne; oznacza to nie są zapisywane do zestawu i nie mogą być używane przez kod w innych zestawach. Mogą one zawierać *opóźnione* członków, co umożliwia typy użycia dostarczane z obszaru potencjalnie nieskończonej informacji. Są one przydatne przy użyciu małego podzbioru źródła danych dużych i połączonych ze sobą.

## <a name="commonly-used-type-providers"></a>Najczęściej używane dostawców typów

Następujące biblioteki powszechnie używane zawierają dostawców typów do różnych celów:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) obejmuje dostawców typów dla formatu JSON, XML, CSV i HTML dokumentu formatów i zasobów.
- [SQLProvider](https://fsprojects.github.io/SQLProvider/) udostępnia silnie typizowane relacji baz danych, za pośrednictwem mapowanie obiektów i LINQ języka F# zapytań dotyczących tych źródeł danych.
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) zestaw dostawców typów dla kompilacji zaewidencjonowanego osadzania T-SQL w języku F#.
- [Dostawca usługi Azure Storage typu](https://fsprojects.github.io/AzureStorageTypeProvider/) zawiera typy używane w obiektach blob platformy Azure, tabele i kolejki, dzięki czemu możesz uzyskać dostęp do tych zasobów bez konieczności określania nazwy zasobów jako ciągi w całym programie.
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html) zawiera **GraphQLProvider**, który zawiera typy, oparte na serwerze GraphQL określony przez adres URL.

W przypadku, gdy to konieczne, możesz [tworzenie własnych niestandardowych dostawców typów](creating-a-type-provider.md), lub odwołaj się do dostawców typów, które zostały utworzone przez innych użytkowników. Na przykład organizacja ma usługę danych dostarczającą dużą i rosnącą liczbę nazwanych zestawów danych, z których każdy ma własny stabilny schemat danych. Można utworzyć dostawcę typów, który odczytuje te schematy i przedstawia programiście najnowsze dostępne zestawy danych w sposób mocno typizowany.

## <a name="see-also"></a>Zobacz także

- [Samouczek: Tworzenie dostawcy typów](creating-a-type-provider.md)
- [Dokumentacja języka F#](../../language-reference/index.md)
- [Visual F#](../../index.md)
