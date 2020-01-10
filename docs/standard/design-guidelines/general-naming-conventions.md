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
ms.openlocfilehash: d1b01fac7368ffeceb554c6f12aecb8f8760fa1d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709338"
---
# <a name="general-naming-conventions"></a>Ogólne konwencje nazewnictwa
W tej sekcji opisano ogólne konwencje nazewnictwa, które odnoszą się do wyboru wyrazu, wytyczne dotyczące używania skrótów i akronimów oraz Zalecenia dotyczące unikania używania nazw specyficznych dla języka.  
  
## <a name="word-choice"></a>Wybór wyrazów  
 **✓ DO** wybrać łatwo odczytać identyfikatora nazwy.  
  
 Na przykład właściwość o nazwie `HorizontalAlignment` ma więcej możliwości odczytywania w języku angielskim niż `AlignmentHorizontal`.  
  
 **✓ DO** Preferuj czytelności za pośrednictwem skrócenia.  
  
 Nazwa właściwości `CanScrollHorizontally` jest lepsza niż `ScrollableX` (przesłonięcie odwołania do osi X).  
  
 **X DO NOT** użyj podkreślenia, łączniki lub innych znaków innych niż alfanumeryczne.  
  
 **X DO NOT** Użyj notacji Węgierskiej.  
  
 **X AVOID** przy użyciu identyfikatorów, które powodują konflikt z słów kluczowych z powszechnie używane języki programowania.  
  
 Zgodnie z regułą 4 Common Language Specification (CLS) wszystkie zgodne Języki muszą zapewniać mechanizm, który umożliwia dostęp do nazwanych elementów, które używają słowa kluczowego tego języka jako identyfikatora. C#na przykład w tym przypadku używa znaku @ jako mechanizmu ucieczki. Jednak nadal dobrym pomysłem jest uniknięcie typowych słów kluczowych, ponieważ jest znacznie trudniejsze użycie metody z sekwencją ucieczki od jednej.  
  
## <a name="using-abbreviations-and-acronyms"></a>Używanie skrótów i akronimów  
 **X DO NOT** Użyj skrótów lub skrótów jako część nazwy identyfikatorów.  
  
 Na przykład użyj `GetWindow`, a nie `GetWin`.  
  
 **X DO NOT** używać żadnych skrótów, które nie są powszechnie zaakceptowany, a nawet wtedy, gdy są one, tylko wtedy, gdy jest to konieczne.  
  
## <a name="avoiding-language-specific-names"></a>Unikanie nazw specyficznych dla języka  
 **✓ DO** użycie nazwy semantycznie interesujące zamiast słowa kluczowe specyficzne dla języka dla nazwy typu.  
  
 Na przykład `GetLength` jest lepszą nazwą niż `GetInt`.  
  
 **✓ DO** Użyj nazwy ogólnej typu CLR, a nie nazwę specyficzne dla języka w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego poza jego typu.  
  
 Na przykład Metoda konwertowana na <xref:System.Int64> powinna mieć nazwę `ToInt64`, a nie `ToLong` (ponieważ <xref:System.Int64> jest nazwą środowiska CLR dla C#aliasu specyficznego `long`). W poniższej tabeli przedstawiono kilka podstawowych typów danych przy użyciu nazw typów CLR (a także odpowiednich nazw typów dla C#, Visual Basic i C++).  
  
|Język C#|Język Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**znak bez znaku**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**bez znaku Short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**Równ**|**niepodpisany int**|**Równ**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**__int64 bez znaku**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Wartość logiczna**|**bool**|**Wartość logiczna**|  
|**char**|**Delikatn**|**wchar_t**|**Delikatn**|  
|**string**|**Ciąg**|**Ciąg**|**Ciąg**|  
|**object**|**Obiekt**|**Obiekt**|**Obiekt**|  
  
 **✓ DO** Użyj nazwą pospolitą, takiego jak `value` lub `item`, zamiast powtarzające się nazwa typu w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego i typ parametru nie jest ważna.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Nazywanie nowych wersji istniejących interfejsów API  
 **✓ DO** Użyj nazwy podobne do starego interfejsu API, podczas tworzenia nowych wersji istniejących interfejsu API.  
  
 Dzięki temu można wyróżnić relacje między interfejsami API.  
  
 **✓ DO** preferowane jest dodanie sufiksu zamiast prefiksu wskazać nową wersję istniejącego interfejsu API.  
  
 Ułatwi to odnajdywanie podczas przeglądania dokumentacji lub korzystania z technologii IntelliSense. Stara wersja interfejsu API zostanie zorganizowana blisko nowych interfejsów API, ponieważ większość przeglądarek i IntelliSense pokazuje identyfikatory w kolejności alfabetycznej.  
  
 **✓ CONSIDER** przy użyciu całkowicie nowe, ale łatwy do rozpoznania identyfikator, zamiast dodawania sufiks lub prefiks.  
  
 **✓ DO** sufiks numeryczny do wskazania użyć nową wersję istniejącego interfejsu API, szczególnie jeśli istniejącej nazwy interfejsu API jest tylko nazwę, która ma sens (tj., jeśli jest standardem branżowym) i dodawania żadnych zrozumiały sufiks (lub zmiana nazwy) nie jest aplikacji Opcja ropriate.  
  
 **X DO NOT** "Ex" (lub podobny) sufiks identyfikatora odróżniający go od wcześniejszej wersji tego samego interfejsu API.  
  
 **✓ DO** Użyj sufiksu "64", wprowadzając wersje interfejsów API, które działają na 64-bitowa liczba całkowita (długich liczb całkowitych) zamiast 32-bitową liczbę całkowitą. To podejście należy wykonać tylko wtedy, gdy istnieje istniejący 32-bitowy interfejs API; nie należy tego robić w przypadku nowych interfejsów API z tylko 64-bitową wersją.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
