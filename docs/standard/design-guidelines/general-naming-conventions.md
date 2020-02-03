---
title: Ogólne konwencje nazewnictwa
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: f8576790a2be08c623807e236d156e0e7f93dd14
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741595"
---
# <a name="general-naming-conventions"></a>Ogólne konwencje nazewnictwa
W tej sekcji opisano ogólne konwencje nazewnictwa, które odnoszą się do wyboru wyrazu, wytyczne dotyczące używania skrótów i akronimów oraz Zalecenia dotyczące unikania używania nazw specyficznych dla języka.

## <a name="word-choice"></a>Wybór wyrazów
 ✔️ Wybierz łatwe DO odczytu nazwy identyfikatorów.

 Na przykład właściwość o nazwie `HorizontalAlignment` ma więcej możliwości odczytywania w języku angielskim niż `AlignmentHorizontal`.

 ✔️ Zwiększaj czytelność w porównaniu z zwięzłości.

 Nazwa właściwości `CanScrollHorizontally` jest lepsza niż `ScrollableX` (przesłonięcie odwołania do osi X).

 ❌ nie używać podkreśleń, łączników ani żadnych innych znaków niealfanumerycznych.

 ❌ nie używać notacji węgierskiej.

 ❌ unikać używania identyfikatorów, które powodują konflikt z słowami kluczowymi powszechnie używanych języków programowania.

 Zgodnie z regułą 4 Common Language Specification (CLS) wszystkie zgodne Języki muszą zapewniać mechanizm, który umożliwia dostęp do nazwanych elementów, które używają słowa kluczowego tego języka jako identyfikatora. C#na przykład w tym przypadku używa znaku @ jako mechanizmu ucieczki. Jednak nadal dobrym pomysłem jest uniknięcie typowych słów kluczowych, ponieważ jest znacznie trudniejsze użycie metody z sekwencją ucieczki od jednej.

## <a name="using-abbreviations-and-acronyms"></a>Używanie skrótów i akronimów
 ❌ nie używaj skrótów ani kontraktów jako części nazw identyfikatorów.

 Na przykład użyj `GetWindow`, a nie `GetWin`.

 ❌ nie używać żadnych akronimów, które nie są powszechnie akceptowane, a nawet jeśli są, tylko w razie potrzeby.

## <a name="avoiding-language-specific-names"></a>Unikanie nazw specyficznych dla języka
 ✔️ należy używać semantycznie interesujących nazw, a nie słów kluczowych charakterystycznych dla języka dla nazw typów.

 Na przykład `GetLength` jest lepszą nazwą niż `GetInt`.

 ✔️ używać generycznej nazwy typu CLR zamiast nazwy specyficznej dla języka, w rzadkich przypadkach, gdy identyfikator nie ma semantyki, poza jej typem.

 Na przykład Metoda konwertowana na <xref:System.Int64> powinna mieć nazwę `ToInt64`, a nie `ToLong` (ponieważ <xref:System.Int64> jest nazwą środowiska CLR dla C#aliasu specyficznego `long`). W poniższej tabeli przedstawiono kilka podstawowych typów danych przy użyciu nazw typów CLR (a także odpowiednich nazw typów dla C#, Visual Basic i C++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**Bajc**|**znak bez znaku**|**Bajc**|
|**short**|**Wybierak**|**short**|**Int16**|
|**ushort**|**UInt16**|**bez znaku Short**|**UInt16**|
|**int**|**Całkowitą**|**int**|**Elementem**|
|**uint**|**Równ**|**niepodpisany int**|**Równ**|
|**long**|**Długo**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**__int64 bez znaku**|**UInt64**|
|**float**|**Wiersz**|**float**|**Wiersz**|
|**double**|**Double**|**double**|**Double**|
|**bool**|**Wartość logiczna**|**bool**|**Wartość logiczna**|
|**char**|**Delikatn**|**wchar_t**|**Delikatn**|
|**string**|**Ciąg**|**Ciąg**|**Ciąg**|
|**object**|**Obiekt**|**Obiekt**|**Obiekt**|

 ✔️ używać nazwy pospolitej, takiej jak `value` lub `item`, zamiast powtarzania nazwy typu, w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego i typ parametru jest nieważny.

## <a name="naming-new-versions-of-existing-apis"></a>Nazywanie nowych wersji istniejących interfejsów API
 ✔️ Użyj nazwy podobnej do starego interfejsu API podczas tworzenia nowych wersji istniejącego interfejsu API.

 Dzięki temu można wyróżnić relacje między interfejsami API.

 ✔️ Preferuj Dodawanie sufiksu zamiast prefiksu, aby wskazać nową wersję istniejącego interfejsu API.

 Ułatwi to odnajdywanie podczas przeglądania dokumentacji lub korzystania z technologii IntelliSense. Stara wersja interfejsu API zostanie zorganizowana blisko nowych interfejsów API, ponieważ większość przeglądarek i IntelliSense pokazuje identyfikatory w kolejności alfabetycznej.

 ✔️ ROZWAŻYĆ użycie zupełnie nowego, ale znaczącego identyfikatora, zamiast dodawania sufiksu lub prefiksu.

 ✔️ Użyj sufiksu liczbowego, aby wskazać nową wersję istniejącego interfejsu API, szczególnie jeśli istniejąca nazwa interfejsu API jest jedyną nazwą, która ma sens (tj. Jeśli jest standardem branżowym) i jeśli Dodawanie dowolnego znaczącego sufiksu (lub zmiana nazwy) nie jest odpowiednią optią z.

 ❌ nie należy używać sufiksu "ex" (lub podobnego) dla identyfikatora w celu odróżnienia go od wcześniejszej wersji tego samego interfejsu API.

 ✔️ Użyj sufiksu "64", wprowadzając wersje interfejsów API, które działają na 64-bitowej liczbie całkowitej (Long Integer) zamiast 32-bit Integer. To podejście należy wykonać tylko wtedy, gdy istnieje istniejący 32-bitowy interfejs API; nie należy tego robić w przypadku nowych interfejsów API z tylko 64-bitową wersją.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
