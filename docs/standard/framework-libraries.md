---
title: Biblioteki Framework
description: "Dowiedz się, jak biblioteki zapewniają implementacji dla wielu typów ogólnych i specyficznych dla aplikacji, algorytmów i funkcji narzędzia."
keywords: .NET, .NET core
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: 6851e7059ca60430e761cebed4fd5040a6a3ee08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="framework-libraries"></a>Biblioteki Framework

.NET ma rozszerzania zestaw standardowych bibliotek klas, określany jako klasy podstawowej biblioteki (podstawowy zestaw) albo bibliotek klas framework (pełny zestaw). Te biblioteki zapewniają implementacji dla wielu typów ogólnych i specyficznych dla aplikacji, algorytmów i funkcji narzędzia. Biblioteki zarówno komercyjnej, jak i społeczności bazując na framework biblioteki klas, zapewniając łatwy w użyciu standardowych bibliotek dla wielu różnych zadań wykonywanych w firmie.

Podzbiór biblioteki te są dostarczane z każdej implementacji .NET. Oczekiwano Base API biblioteki klas (BCL) z implementacji .NET, zarówno ponieważ deweloperzy będą potrzebne, a popularnych bibliotek będą potrzebne do uruchomienia. Specyficzny dla aplikacji biblioteki powyżej BCL, takich jak ASP.NET, nie będzie dostępny dla wszystkich implementacji .NET.

## <a name="base-class-libraries"></a>Biblioteki klasy podstawowej

BCL zapewnia najbardziej podstawowym typy i funkcje narzędzia i jest podstawą wszystkich innych bibliotek klas .NET. One mają na celu dostarczenie bardzo ogólne implementacje bez żadnych odchylenia do dowolnego obciążenia. Wydajność jest zawsze ważną kwestią, ponieważ aplikacje łączyli konkretne zasady, takie jak małych opóźnieniach do wysokiej przepustowości lub do użycia procesora CPU małej ilości pamięci. Te biblioteki mają być zazwyczaj wysokiej wydajności i podejmij podejście podstaw bliski zgodnie z tymi różnych problemów z wydajnością. Dla większości aplikacji ta metoda została dość pomyślnie.

## <a name="primitive-types"></a>Typy pierwotne

.NET zawiera zbiór typy pierwotne, które są używane (w różnym stopniu) w wszystkie programy. Te typy zawierać dane, takie jak numery, ciągów i bajtów dowolnych obiektów. W języku C# zawiera słowa kluczowe dla tych typów. Przykładowy zestaw tych typów jest poniżej dopasowania słów kluczowych C#.

* <xref:System.Object?displayProperty=nameWithType>([obiektu](../csharp/language-reference/keywords/object.md))-system typów ultimate klasy podstawowej w środowisku CLR. Jest elementem głównym hierarchii typów.
* <xref:System.Int16?displayProperty=nameWithType>([krótki](../csharp/language-reference/keywords/short.md))-A 16-bitowych podpisany typu Liczba całkowita. Niepodpisane <xref:System.UInt16> również istnieje.
* <xref:System.Int32?displayProperty=nameWithType>([int](../csharp/language-reference/keywords/int.md))-A 32-bitowej podpisanej typu Liczba całkowita. Niepodpisane [UInt32](../csharp/language-reference/keywords/uint.md) również istnieje.
* <xref:System.Single?displayProperty=nameWithType>([float](../csharp/language-reference/keywords/float.md)) — typ zmiennoprzecinkowy A 32-bitowych.
* <xref:System.Decimal?displayProperty=nameWithType>([dziesiętną](../csharp/language-reference/keywords/decimal.md))-A 128-bitowego typu decimal.
* <xref:System.Byte?displayProperty=nameWithType>([bajtów](../csharp/language-reference/keywords/byte.md))-niepodpisane 8-bitową liczbę całkowitą reprezentującą bajtów pamięci.
* <xref:System.Boolean?displayProperty=nameWithType>([bool](../csharp/language-reference/keywords/bool.md)) — typu boolean, która reprezentuje `true` lub `false`.
* <xref:System.Char?displayProperty=nameWithType>([char](../csharp/language-reference/keywords/char.md))-A 16-bitowych typ liczbowy reprezentujący znak Unicode.
* <xref:System.String?displayProperty=nameWithType>([ciąg](../csharp/language-reference/keywords/string.md))-reprezentuje ciąg znaków. Inne niż `char[]`, ale umożliwia indeksowania w poszczególnych `char` w `string`.

## <a name="data-structures"></a>Struktury danych

.NET zawiera zestaw struktur danych, które są narzędzie baz prawie każdej aplikacji .NET. Te są kolekcjami przede wszystkim, ale także inne typy.

*   <xref:System.Array>-Reprezentuje tablicę silnie typów obiektów, które mogą być udostępniane przez indeks. Ma stały rozmiar, na jego konstrukcji.
*   <xref:System.Collections.Generic.List%601>-Reprezentuje silnie typizowaną listę obiektów, które mogą być udostępniane przez indeks. Automatycznie zmieniany jest zgodnie z potrzebami.
*   <xref:System.Collections.Generic.Dictionary%602>-Reprezentuje kolekcję wartości, które są indeksowane według klucza. Wartości są dostępne za pośrednictwem klucza. Automatycznie zmieniany jest zgodnie z potrzebami.
*   <xref:System.Uri>— Umożliwia reprezentację obiektu identyfikator uniform resource identifier (URI) i łatwy dostęp do części identyfikatora URI.
*   <xref:System.DateTime>-Reprezentuje moment w czasie, zwykle wyrażone jako datę i godzinę.

## <a name="utility-apis"></a>Narzędzie interfejsów API

.NET zawiera zestaw interfejsów API, które zawierają wiele zadań ważne funkcje narzędzia.

*   <xref:System.Net.Http.HttpClient>— Interfejs API do wysyłania żądań HTTP i odbierania odpowiedzi HTTP z zasobu identyfikowanego przez identyfikator URI.
*   <xref:System.Xml.Linq.XDocument>— Interfejs API do ładowania i badania dokumentów XML za pomocą LINQ.
*   <xref:System.IO.StreamReader>— Interfejs API do odczytywania plików (<xref:System.IO.StringWriter>) może służyć do zapisania plików.

## <a name="app-model-apis"></a>Interfejsy API modelu aplikacji

Istnieje wiele modeli aplikacji, które mogą być używane z platformy .NET, które są udostępniane przez kilka firm.

*   [ASP.NET](http://asp.net) — zapewnia platformę sieci web do tworzenia witryn sieci Web i usług. Obsługiwane w systemach Windows, Linux i macOS (zależy od wersji platformy ASP.NET).
