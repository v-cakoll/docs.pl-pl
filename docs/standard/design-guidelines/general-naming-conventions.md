---
title: Ogólne konwencje nazewnictwa
description: Użyj ogólnych konwencji nazewnictwa dotyczących wyboru wyrazów, wytycznych dotyczących używania skrótów i akronimów oraz wskazówki dotyczące unikania nazw specyficznych dla języka.
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
ms.openlocfilehash: b7f06a57c57800afcfa7febf9452094b4ad5ddc1
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769083"
---
# <a name="general-naming-conventions"></a>Ogólne konwencje nazewnictwa

W tej sekcji opisano ogólne konwencje nazewnictwa, które odnoszą się do wyboru wyrazu, wytyczne dotyczące używania skrótów i akronimów oraz Zalecenia dotyczące unikania używania nazw specyficznych dla języka.

## <a name="word-choice"></a>Wybór wyrazów
 ✔️ Wybierz łatwe DO odczytu nazwy identyfikatorów.

 Na przykład właściwość o nazwie `HorizontalAlignment` jest bardziej czytelna w języku angielskim niż `AlignmentHorizontal` .

 ✔️ Zwiększaj czytelność w porównaniu z zwięzłości.

 Nazwa właściwości `CanScrollHorizontally` jest lepsza niż `ScrollableX` (przesłonięcie odwołania do osi X).

 ❌NIE używaj podkreśleń, łączników ani żadnych innych znaków niealfanumerycznych.

 ❌NIE używaj notacji węgierskiej.

 ❌UNIKAj używania identyfikatorów, które powodują konflikt z słowami kluczowymi powszechnie używanych języków programowania.

 Zgodnie z regułą 4 Common Language Specification (CLS) wszystkie zgodne Języki muszą zapewniać mechanizm, który umożliwia dostęp do nazwanych elementów, które używają słowa kluczowego tego języka jako identyfikatora. Na przykład w języku C# w tym przypadku używa znaku @. Jednak nadal dobrym pomysłem jest uniknięcie typowych słów kluczowych, ponieważ jest znacznie trudniejsze użycie metody z sekwencją ucieczki od jednej.

## <a name="using-abbreviations-and-acronyms"></a>Używanie skrótów i akronimów
 ❌NIE używaj skrótów ani kontraktów jako części nazw identyfikatorów.

 Na przykład użyj `GetWindow` zamiast `GetWin` .

 ❌Nie używaj żadnych akronimów, które nie są powszechnie akceptowane, a nawet jeśli są, tylko w razie potrzeby.

## <a name="avoiding-language-specific-names"></a>Unikanie nazw specyficznych dla języka
 ✔️ należy używać semantycznie interesujących nazw, a nie słów kluczowych charakterystycznych dla języka dla nazw typów.

 Na przykład `GetLength` to lepsza nazwa niż `GetInt` .

 ✔️ używać generycznej nazwy typu CLR zamiast nazwy specyficznej dla języka, w rzadkich przypadkach, gdy identyfikator nie ma semantyki, poza jej typem.

 Na przykład Metoda konwertowana na <xref:System.Int64> powinna mieć nazwę `ToInt64` , nie `ToLong` (ponieważ <xref:System.Int64> jest nazwą środowiska CLR dla aliasu specyficznego dla języka C# `long` ). W poniższej tabeli przedstawiono kilka podstawowych typów danych przy użyciu nazw typów CLR (a także odpowiednich nazw typów dla języków C#, Visual Basic i C++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**SByte**|**SByte**|**char**|**SByte**|
|**Bajc**|**Bajc**|**unsigned char**|**Bajc**|
|**short**|**Wybierak**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Liczba całkowita**|**int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**długi**|**Długo**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**__int64 bez znaku**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**Double**|**double**|**Double**|
|**bool**|**Wartość logiczna**|**bool**|**Wartość logiczna**|
|**char**|**Delikatn**|**wchar_t**|**Delikatn**|
|**parametry**|**Ciąg**|**Ciąg**|**Ciąg**|
|**Stream**|**Obiekt**|**Obiekt**|**Obiekt**|

 ✔️ używać nazwy pospolitej, takiej jak `value` lub `item` , zamiast powtarzania nazwy typu, w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego i typ parametru jest nieważny.

## <a name="naming-new-versions-of-existing-apis"></a>Nazywanie nowych wersji istniejących interfejsów API
 ✔️ Użyj nazwy podobnej do starego interfejsu API podczas tworzenia nowych wersji istniejącego interfejsu API.

 Dzięki temu można wyróżnić relacje między interfejsami API.

 ✔️ Preferuj Dodawanie sufiksu zamiast prefiksu, aby wskazać nową wersję istniejącego interfejsu API.

 Ułatwi to odnajdywanie podczas przeglądania dokumentacji lub korzystania z technologii IntelliSense. Stara wersja interfejsu API zostanie zorganizowana blisko nowych interfejsów API, ponieważ większość przeglądarek i IntelliSense pokazuje identyfikatory w kolejności alfabetycznej.

 ✔️ ROZWAŻYĆ użycie zupełnie nowego, ale znaczącego identyfikatora, zamiast dodawania sufiksu lub prefiksu.

 ✔️ Użyj sufiksu liczbowego, aby wskazać nową wersję istniejącego interfejsu API, szczególnie jeśli istniejąca nazwa interfejsu API jest jedyną nazwą, która ma sens (tj. Jeśli jest standardem branżowym) i jeśli dodanie dowolnego znaczącego sufiksu (lub zmiana nazwy) nie jest odpowiednią opcją.

 ❌NIE używaj sufiksu "ex" (lub podobnego) dla identyfikatora, aby odróżnić go od wcześniejszej wersji tego samego interfejsu API.

 ✔️ Użyj sufiksu "64", wprowadzając wersje interfejsów API, które działają na 64-bitowej liczbie całkowitej (Long Integer) zamiast 32-bit Integer. To podejście należy wykonać tylko wtedy, gdy istnieje istniejący 32-bitowy interfejs API; nie należy tego robić w przypadku nowych interfejsów API z tylko 64-bitową wersją.

 *Fragmenty &copy; 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz też

- [Framework — zalecenia dotyczące projektowania](index.md)
- [Wskazówki dotyczące nazewnictwa](naming-guidelines.md)
- [Konwencje nazewnictwa platformy .NET dla EditorConfig](/visualstudio/ide/editorconfig-naming-conventions)
