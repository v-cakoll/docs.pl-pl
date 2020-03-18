---
title: Biblioteki platformy
description: Dowiedz się, jak biblioteki zapewniają implementacje dla wielu typów ogólnych i specyficznych dla aplikacji, algorytmów i funkcji użytkowych.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: d4444b6d080afa92a4e7fd9f30c5f9358f02f0ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159237"
---
# <a name="framework-libraries"></a>Biblioteki platformy

.NET ma ekspansywny standardowy zestaw bibliotek klas, nazywany bibliotekami klas podstawowych (zestaw podstawowy) lub bibliotekami klas framework (kompletny zestaw). Biblioteki te zapewniają implementacje dla wielu typów ogólnych i specyficznych dla aplikacji, algorytmów i funkcji narzędzia. Biblioteki komercyjne i społeczne są oparte na bibliotekach klas framework, zapewniając łatwe w użyciu gotowe biblioteki do szerokiego zestawu zadań obliczeniowych.

Podzbiór tych bibliotek są dostarczane z każdej implementacji .NET. Interfejsy API biblioteki klas podstawowych (BCL) są oczekiwane z dowolną implementacją .NET, zarówno dlatego, że deweloperzy będą chcieli je, jak i dlatego, że popularne biblioteki będą potrzebować ich do uruchomienia. Biblioteki specyficzne dla aplikacji powyżej listy BCL, takie jak ASP.NET, nie będą dostępne we wszystkich implementacjach .NET.

## <a name="base-class-libraries"></a>Biblioteki klas podstawowych

BCL zapewnia najbardziej podstawowe typy i funkcje użytkowe i są podstawą wszystkich innych bibliotek klas .NET. Mają one na celu zapewnienie bardzo ogólnych implementacji bez stronniczości do jakiegokolwiek obciążenia. Wydajność jest zawsze ważnym czynnikiem, ponieważ aplikacje mogą preferować określonej zasady, takie jak małe opóźnienia do wysokiej przepływności lub niskiej pamięci do niskiego użycia procesora CPU. Biblioteki te mają być ogólnie wysokiej wydajności i podjąć podejście śródziemia zgodnie z tymi różnymi problemami dotyczącymi wydajności. W przypadku większości aplikacji takie podejście było bardzo udane.

## <a name="primitive-types"></a>Typy pierwotne

.NET zawiera zestaw typów pierwotnych, które są używane (w różnym stopniu) we wszystkich programach. Typy te zawierają dane, takie jak liczby, ciągi, bajty i dowolne obiekty. Język C# zawiera słowa kluczowe dla tych typów. Przykładowy zestaw tych typów jest wymieniony poniżej, z pasującymi słowami kluczowymi Języka C#.

* <xref:System.Object?displayProperty=nameWithType>([object](../csharp/language-reference/builtin-types/reference-types.md#the-object-type)) - Ostateczna klasa podstawowa w systemie typu CLR. Jest to katalog główny hierarchii typów.
* <xref:System.Int16?displayProperty=nameWithType>([krótki](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - 16-bitowy podpisany typ liczby całkowitej. Niepodpisany <xref:System.UInt16> również istnieje.
* <xref:System.Int32?displayProperty=nameWithType>([int](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - 32-bitowy typ liczby całkowitej z podpisem. Niepodpisany [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) również istnieje.
* <xref:System.Single?displayProperty=nameWithType>([float](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) - 32-bitowy typ zmiennoprzecinkowy.
* <xref:System.Decimal?displayProperty=nameWithType>[(dziesiętne)](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)- 128-bitowy typ dziesiętny.
* <xref:System.Byte?displayProperty=nameWithType>([bajt](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - Niepodpisana 8-bitowa liczba całkowita reprezentująca bajt pamięci.
* <xref:System.Boolean?displayProperty=nameWithType>([bool](../csharp/language-reference/builtin-types/bool.md)) - Typ logiczny, który reprezentuje `true` lub `false`.
* <xref:System.Char?displayProperty=nameWithType>([char](../csharp/language-reference/builtin-types/char.md)) - 16-bitowy typ numeryczny reprezentujący znak Unicode.
* <xref:System.String?displayProperty=nameWithType>([ciąg](../csharp/language-reference/builtin-types/reference-types.md#the-string-type)) - Reprezentuje serię znaków. Inny niż `char[]`, ale umożliwia indeksowanie do każdej osoby `char` w . `string`

## <a name="data-structures"></a>Struktury danych

.NET zawiera zestaw struktur danych, które są konie robocze prawie wszystkich aplikacji .NET. Są to głównie kolekcje, ale również inne typy.

* <xref:System.Array>- Reprezentuje tablicę silnie typów obiektów, które są dostępne przez indeks. Ma stałą wielkość, na jego budowę.
* <xref:System.Collections.Generic.List%601>- Reprezentuje silnie typizoną listę obiektów, do których można uzyskać dostęp za pomocą indeksu. W razie potrzeby zostanie automatycznie zmniejszony rozmiar.
* <xref:System.Collections.Generic.Dictionary%602>- Reprezentuje kolekcję wartości, które są indeksowane przez klucz. Wartości są dostępne za pomocą klucza. W razie potrzeby zostanie automatycznie zmniejszony rozmiar.
* <xref:System.Uri>- Zapewnia reprezentację obiektu jednolitego identyfikatora zasobu (URI) i łatwy dostęp do części identyfikatora URI.
* <xref:System.DateTime>- Reprezentuje moment w czasie, zazwyczaj wyrażone jako data i godzina dnia.

## <a name="utility-apis"></a>Interfejsy API narzędzia

.NET zawiera zestaw interfejsów API narzędzia, które zapewniają funkcje dla wielu ważnych zadań.

* <xref:System.Net.Http.HttpClient>- Interfejs API do wysyłania żądań HTTP i odbierania odpowiedzi HTTP z zasobu identyfikowanego przez identyfikator URI.
* <xref:System.Xml.Linq.XDocument>- Interfejs API do ładowania i wykonywania zapytań dotyczących dokumentów XML za pomocą LINQ.
* <xref:System.IO.StreamReader>- API do odczytywania plików.
* <xref:System.IO.StreamWriter>- API do zapisywania plików.

## <a name="app-model-apis"></a>Interfejsy API modelu aplikacji

Istnieje wiele modeli aplikacji, które mogą być używane z .NET, dostarczone przez kilka firm.

* [ASP.NET](https://www.asp.net) — zapewnia strukturę sieci Web do tworzenia witryn i usług sieci Web. Obsługiwane w systemach Windows, Linux i macOS (zależy od wersji ASP.NET).
