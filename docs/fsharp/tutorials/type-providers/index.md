---
title: "Dostawcy typów"
description: "Dowiedz się, jak dostawcy typów F # jest składnikiem, który zawiera typy, właściwości i metod do użycia w programach."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
ms.openlocfilehash: f721b5b378bf70fb594cad66bd90bd96a0320ee2
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="type-providers"></a>Dostawcy typów

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](https://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

Dostawca typów języka F# to składnik, który dostarcza typy, właściwości i metody używane w programie. Dostawcy typów są znaczącą częścią obsługi programowania z dużą ilością informacji w języku F# 3.0. Kluczem do programowania z dużą ilością informacji jest wyeliminowanie barier w pracy z różnymi źródłami informacji w Internecie i nowoczesnych środowiskach w przedsiębiorstwach. Jedną ze znaczących barier w dołączaniu źródła informacji do programu jest potrzeba przedstawienia informacji jako typów, właściwości i metod, których można używać w środowisku języka programowania. Ręczne pisanie tych typów jest bardzo czasochłonne i trudne pod względem organizacyjnym. Powszechną alternatywą jest użycie generatora kodu, który dodaje pliki do projektu, jednak konwencjonalne typy generowania kodu nie integrują się poprawnie w eksploracyjnych trybach programowania obsługiwanych przez język F#, ponieważ wygenerowany kod musi być zastępowany za każdym razem, gdy odwołanie do usługi jest zmieniane.

Typy dostarczanie przez dostawców typów języka F# są zazwyczaj oparte na zewnętrznych źródłach informacji. Na przykład dostawca typów języka F# dla języka SQL dostarcza typy, właściwości i metody, które są wymagane do pracy bezpośrednio z tabelami dowolnej bazy danych SQL, do której użytkownik ma dostęp. Podobnie dostawcy typów dla usług sieci Web WSDL dostarczają typy, właściwości i metody potrzebne do bezpośredniej pracy z dowolnymi usługami sieci Web WSDL.

Zestaw typów, właściwości i metod dostarczony przez dostawcę typów języka F# może zależeć od parametrów podanych w kodzie programu. Na przykład dostawca typów może dostarczyć różne typy, w zależności od parametrów połączenia lub adresu URL usługi. W ten sposób przestrzeń informacji dostępna w parametrach połączenia lub adresie URL jest bezpośrednio zintegrowana z programem. Dostawca typów może również zagwarantować, że grupy typów są rozszerzane jedynie na żądanie, co oznacza, że są one rozszerzane, tylko jeśli do danego typu odwołuje się program. Umożliwia to bezpośrednią integrację na żądanie przestrzeni informacji o wielkiej skali, takich jak sieciowe rynki danych, w sposób silnie typizowany.

Język F# zawiera kilku wbudowanych dostawców typów przeznaczonych do obsługi popularnych internetowych i firmowych usług danych. Ci dostawcy typów oferują prosty i regularny dostęp do relacyjnych baz danych SQL oraz sieciowych usług OData i WSDL, a także obsługują używanie zapytań LINQ języka F# dla tych źródeł danych.

Gdy jest to konieczne, można tworzyć własnych niestandardowych dostawców typów lub odwoływać się do dostawców typów utworzonych przez innych użytkowników. Na przykład organizacja ma usługę danych dostarczającą dużą i rosnącą liczbę nazwanych zestawów danych, z których każdy ma własny stabilny schemat danych. Można utworzyć dostawcę typów, który odczytuje te schematy i przedstawia programiście najnowsze dostępne zestawy danych w sposób mocno typizowany.


## <a name="related-topics"></a>Tematy pokrewne


|Tytuł|Opis|
|-----|-----------|
|[Wskazówki: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](accessing-a-sql-database.md)|Opis sposobu używania dostawcy typów SqlDataConnection w celu uzyskania dostępu do tabel i procedur składowanych w bazie danych SQL na podstawie parametrów połączenia umożliwiających bezpośrednie połączenie z bazą danych. Dostęp odbywa się przy użyciu mapowania LINQ to SQL.|
|[Wskazówki: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów i jednostek](accessing-a-sql-database-entities.md)|Opis sposobu używania dostawcy typów SqlEntityConnection w celu uzyskania dostępu do tabel i procedur składowanych w bazie danych SQL na podstawie parametrów połączenia umożliwiających bezpośrednie połączenie z bazą danych. Dostęp odbywa się przy użyciu mapowania LINQ to Entities. Ta metoda działa z dowolną bazą danych, ale w przykładzie użyto programu SQL Server.|
|[Wskazówki: Uzyskiwanie dostępu do usługi OData za pomocą dostawców typów](accessing-an-odata-service.md)|Opis sposobu użycia dostawcy typów ODataService w celu uzyskania dostępu do usługi OData w silnie typizowany sposób na podstawie adresu URL usługi.|
|[Wskazówki: Uzyskiwanie dostępu do usługi sieci Web za pomocą dostawców typów](accessing-a-web-service.md)|Opis sposobu użycia dostawcy typów WsdlService w celu uzyskania dostępu do usługi sieci Web WSDL w silnie typizowany sposób na podstawie adresu URL usługi.|
|[Wskazówki: Generowanie F & 35; Typy z pliku DBML](generating-fsharp-types-from-dbml.md)|Opis sposobu użycia dostawcy typów DbmlFile w celu uzyskania dostępu do tabel i procedur składowanych w bazie danych SQL na podstawie pliku DBML dostarczającego specyfikację schematu bazy danych LINQ to SQL.|
|[Wskazówki: Generowanie F & 35; Typy za pomocą pliku schematu EDMX](generating-fsharp-types-from-edmx.md)|Opis sposobu użycia dostawcy typów EdmxFile w celu uzyskania dostępu do tabel i procedur składowanych bazy danych SQL na podstawie pliku EDMX dostarczającego specyfikację schematu Entity Framework.|
|[Samouczek: Tworzenie dostawcy typów](creating-a-type-provider.md)|Informacje dotyczące pisania własnych niestandardowych dostawców typów.|
|[Zabezpieczenia dostawcy typów](type-provider-security.md)|Omówienie zagadnień dotyczących zabezpieczeń podczas opracowywania dostawców typów.|
|[Rozwiązywanie problemów z dostawcami typów](troubleshooting-type-providers.md)|Informacje dotyczące typowych problemów, które mogą pojawić się podczas pracy z dostawcami typów, oraz propozycje ich rozwiązań.|

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](../../language-reference/index.md)

[Visual F#](../../index.md)
