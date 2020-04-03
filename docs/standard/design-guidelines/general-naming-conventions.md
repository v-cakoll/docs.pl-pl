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
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635916"
---
# <a name="general-naming-conventions"></a>Ogólne konwencje nazewnictwa

W tej sekcji opisano ogólne konwencje nazewnictwa, które odnoszą się do wyboru wyrazów, wskazówki dotyczące używania skrótów i akronimów oraz zalecenia dotyczące unikania używania nazw specyficznych dla języka.

## <a name="word-choice"></a>Wybór wyrazu
 ✔️ wybrać łatwe do odczytania nazwy identyfikatorów.

 Na przykład właściwość `HorizontalAlignment` o nazwie jest `AlignmentHorizontal`bardziej czytelna w języku angielskim niż .

 ✔️ czy preferuje czytelność ponad zwięzłość.

 Nazwa `CanScrollHorizontally` właściwości jest `ScrollableX` lepsza niż (niejasne odwołanie do osi X).

 ❌NIE używaJ podkreśleń, łączników ani innych znaków niealphanumerycznych.

 ❌NIE używaj notacji węgierskiej.

 ❌UNIKAJ używania identyfikatorów, które są w konflikcie ze słowami kluczowymi powszechnie używanych języków programowania.

 Zgodnie z regułą 4 specyfikacji języka wspólnego (CLS), wszystkie zgodne języki muszą zapewniać mechanizm, który umożliwia dostęp do nazwanych elementów, które używają słowa kluczowego tego języka jako identyfikatora. C#, na przykład używa znaku @jako mechanizmu ucieczki w tym przypadku. Jednak nadal jest dobrym pomysłem, aby uniknąć typowych słów kluczowych, ponieważ jest znacznie trudniejsze do użycia metody z sekwencji ucieczki niż jeden bez niego.

## <a name="using-abbreviations-and-acronyms"></a>Używanie skrótów i akronimów
 ❌NIE używaJ skrótów lub skurczów jako części nazw identyfikatorów.

 Na przykład `GetWindow` użyj, `GetWin`a nie .

 ❌NIE używaj żadnych akronimów, które nie są powszechnie akceptowane, a nawet jeśli są, tylko wtedy, gdy jest to konieczne.

## <a name="avoiding-language-specific-names"></a>Unikanie nazw specyficznych dla języka
 ✔️ do używania semantycznie interesujących nazw, a nie słów kluczowych specyficznych dla języka dla nazw typów.

 Na przykład `GetLength` jest lepszą `GetInt`nazwą niż .

 ✔️ DO używać ogólnej nazwy typu CLR, a nie nazwy specyficznej dla języka, w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego poza jego typem.

 Na przykład metoda konwersji <xref:System.Int64> na `ToInt64`powinien `ToLong` być <xref:System.Int64> nazwany , nie (ponieważ jest nazwą `long`CLR dla aliasu specyficznego C#). W poniższej tabeli przedstawiono kilka podstawowych typów danych przy użyciu nazw typów CLR (a także odpowiadające im nazwy typów dla języka C#, Visual Basic i C++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**Sbyte**|**Sbyte**|**char**|**Sbyte**|
|**Bajtów**|**Byte**|**unsigned char**|**Byte**|
|**short**|**Krótki**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**Liczba całkowita**|**int**|**Int32**|
|**Uint**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Długi**|**__int64**|**Int64 ( int64 )**|
|**ulong**|**UInt64**|**niepodpisane __int64**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**Podwójne**|**double**|**Podwójne**|
|**bool**|**Wartość logiczna**|**bool**|**Wartość logiczna**|
|**char**|**Char**|**wchar_t**|**Char**|
|**Ciąg**|**Ciąg**|**Ciąg**|**Ciąg**|
|**obiekt**|**Obiektu**|**Obiektu**|**Obiektu**|

 ✔️ DO używać nazwy pospolitej, takiej jak `value` lub `item`, zamiast powtarzać nazwę typu, w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego, a typ parametru nie jest ważny.

## <a name="naming-new-versions-of-existing-apis"></a>Nazywanie nowych wersji istniejących interfejsów API
 ✔️ DO używać nazwy podobnej do starego interfejsu API podczas tworzenia nowych wersji istniejącego interfejsu API.

 Pomaga to wyróżnić relację między interfejsami API.

 ✔️ DO wolą dodawać sufiks, a nie prefiks, aby wskazać nową wersję istniejącego interfejsu API.

 Pomoże to odnajdować podczas przeglądania dokumentacji lub przy użyciu technologii IntelliSense. Stara wersja interfejsu API zostanie zorganizowana w pobliżu nowych interfejsów API, ponieważ większość przeglądarek i intellisense pokazuje identyfikatory w kolejności alfabetycznej.

 ✔️ ROZWAŻ użycie zupełnie nowego, ale znaczącego identyfikatora, zamiast dodawania sufiksu lub prefiksu.

 ✔️ DO użyj sufiksu numerycznego, aby wskazać nową wersję istniejącego interfejsu API, szczególnie jeśli istniejąca nazwa interfejsu API jest jedyną nazwą, która ma sens (tj. jeśli jest to standard branżowy) i jeśli dodanie dowolnego znaczącego sufiksu (lub zmiana nazwy) nie jest odpowiednią opcją.

 ❌NIE należy używać sufiksu "Ex" (lub podobnego) identyfikatora, aby odróżnić go od wcześniejszej wersji tego samego interfejsu API.

 ✔️ DO używać sufiksu "64" podczas wprowadzania wersji interfejsów API, które działają na 64-bitowej całkowitej (długiej liczby całkowitej) zamiast 32-bitowej liczby całkowitej. Wystarczy przyjąć takie podejście tylko wtedy, gdy istnieje istniejący 32-bitowy interfejs API; nie rób tego dla zupełnie nowych interfejsów API z tylko wersją 64-bitową.

 *Części &copy; 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowany 22 października 2008 przez Addison-Wesley Professional w ramach microsoft windows development series.*

## <a name="see-also"></a>Zobacz też

- [Framework — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [Konwencje nazewnictwa platformy .NET dla EditorConfig](/visualstudio/ide/editorconfig-naming-conventions)
