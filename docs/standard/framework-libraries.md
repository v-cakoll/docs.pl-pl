---
title: Biblioteki platformy
description: Dowiedz się, jak dostarczać implementacje bibliotek dla wielu typów ogólnych i specyficznych dla aplikacji, algorytmów i funkcjonalności narzędzie.
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: 494ac194fe8dc9554c6e0d1d87ba2ed613d1d16b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663226"
---
# <a name="framework-libraries"></a>Biblioteki platformy

.NET zawiera szerokiej gamy standardowych bibliotek klas, określane jako bibliotek klas bazowych (podstawowy zestaw) lub biblioteki klas framework (kompletny zestaw). Te biblioteki zapewniają implementacje dla wielu typów ogólnych i specyficznych dla aplikacji, algorytmów i funkcjonalności narzędzie. Komercyjnych i społeczności biblioteki są oparte na bibliotek klas framework, zapewniając łatwy w użyciu standardowych bibliotek dla wielu różnych zadań wykonywanych w firmie.

Podzbiór biblioteki te są dostarczane z każdej implementacji .NET. Podstawowej klasy biblioteki (BCL) interfejsy API powinny z implementacji .NET, zarówno ponieważ deweloperzy będą chcieli je i popularnych bibliotek będą one potrzebne do uruchomienia. Biblioteki charakterystyczne dla aplikacji powyżej BCL, takich jak ASP.NET, nie będzie dostępny w wszystkich implementacji .NET.

## <a name="base-class-libraries"></a>Biblioteki klas bazowych

BCL udostępnia najbardziej podstawowe typy i funkcje narzędzia i są podstawą wszystkie inne biblioteki klas platformy .NET. One na celu dostarczać implementacje bardzo ogólny bez żadnych odchylenie do dowolnych obciążeń. Wydajność zawsze jest ważną kwestią, ponieważ aplikacje preferować konkretne zasady, takie jak o małych opóźnieniach do wysokiej przepływności lub małej ilości pamięci do użycia procesora CPU na niskim. Biblioteki te są przeznaczone do ogólnie można o wysokiej wydajności i podejścia podstaw bliski według tych różnych problemów z wydajnością. W przypadku większości aplikacji ta metoda zakończy się powodzeniem dość.

## <a name="primitive-types"></a>Typy pierwotne

.NET zawiera zestaw typów pierwotnych, które są używane (w różnym stopniu) we wszystkich programach. Te typy zawierać dane, takie jak liczby, ciągi, bajtów i dowolnych obiektów. C# Język zawiera słowa kluczowe dla tych typów. Przykładowy zestaw te typy są wymienione poniżej pod warunkiem za pomocą dopasowywania C# słów kluczowych.

* <xref:System.Object?displayProperty=nameWithType> ([obiektu](../csharp/language-reference/keywords/object.md)) — system typów ultimate klasy podstawowej w środowisku CLR. Jest głównym hierarchii typów.
* <xref:System.Int16?displayProperty=nameWithType> ([krótki](../csharp/language-reference/builtin-types/integral-numeric-types.md))-16-bitowe podpisane typu Liczba całkowita. Niepodpisane <xref:System.UInt16> istnieje również.
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/builtin-types/integral-numeric-types.md))-32-bitowe podpisane typu Liczba całkowita. Niepodpisane [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) istnieje również.
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) — typ zmiennoprzecinkowy 32-bitowych.
* <xref:System.Decimal?displayProperty=nameWithType> ([dziesiętna](../csharp/language-reference/builtin-types/floating-point-numeric-types.md))-128-bitowego typu dziesiętnego.
* <xref:System.Byte?displayProperty=nameWithType> ([bajtów](../csharp/language-reference/builtin-types/integral-numeric-types.md))-8-bitowa liczba całkowita bez znaku reprezentuje bajtów pamięci.
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/keywords/bool.md)) — typu boolean, która reprezentuje `true` lub `false`.
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/keywords/char.md))-16-bitowych typu liczbowego, który reprezentuje znak Unicode.
* <xref:System.String?displayProperty=nameWithType> ([ciąg](../csharp/language-reference/keywords/string.md))-reprezentuje serię znaków. Różni się od `char[]`, ale umożliwia indeksowanie w poszczególnych osób `char` w `string`.

## <a name="data-structures"></a>Struktury danych

.NET zawiera zestaw struktur danych, które są narzędzie baz niemal wszystkich aplikacji .NET. To są kolekcjami przede wszystkim, ale także innych typów.

* <xref:System.Array> -Reprezentuje tablicę obiektów silnie typy, które mogą być udostępniane przez indeks. Ma stały rozmiar, na jego konstrukcji.
* <xref:System.Collections.Generic.List%601> -Reprezentuje silnie typizowaną listę obiektów, które mogą być udostępniane przez indeks. Automatycznie zmiany rozmiaru zgodnie z potrzebami.
* <xref:System.Collections.Generic.Dictionary%602> -Reprezentuje kolekcję wartości, które są indeksowane według klucza. Wartości są dostępne za pośrednictwem klucza. Automatycznie zmiany rozmiaru zgodnie z potrzebami.
* <xref:System.Uri> -Zawiera reprezentację obiektu jednolity identyfikator zasobów (URI) oraz łatwy dostęp do elementów identyfikatorów URI.
* <xref:System.DateTime> -Reprezentuje moment w czasie, zwykle wyrażona jako datę i godzinę.

## <a name="utility-apis"></a>Narzędzia interfejsów API

.NET zawiera zbiór narzędzia interfejsów API, które udostępniają funkcje wiele istotnych zadań.

* <xref:System.Net.Http.HttpClient> -Interfejs API do wysyłania żądań HTTP i odbierania odpowiedzi HTTP z zasobu zidentyfikowanego z użyciem identyfikatora URI.
* <xref:System.Xml.Linq.XDocument> -Interfejs API, ładowanie i wykonywanie zapytań względem dokumentów XML za pomocą LINQ.
* <xref:System.IO.StreamReader> -Interfejs API, do odczytywania plików. 
* <xref:System.IO.StreamWriter> -Interfejs API, do zapisywania plików.

## <a name="app-model-apis"></a>Interfejsy API modelu aplikacji

Istnieje wiele modeli aplikacji, które mogą służyć za pomocą platformy .NET, dostarczone przez kilka przedsiębiorstw.

* [ASP.NET](https://www.asp.net) — udostępnia platformę internetową do tworzenia witryn sieci Web i usług. Obsługiwana na Windows, Linux i macOS (w zależności od wersji programu ASP.NET).
