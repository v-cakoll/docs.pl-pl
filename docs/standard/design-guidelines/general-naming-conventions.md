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
author: KrzysztofCwalina
ms.openlocfilehash: ae1b7ce83f6698cef470aabf07a12d89042ab8a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667690"
---
# <a name="general-naming-conventions"></a>Ogólne konwencje nazewnictwa
W tej sekcji opisano ogólne konwencje nazewnictwa, które odnoszą się do wybranego słowa wskazówki na temat używania skrótów i akronimów i zalecenia dotyczące sposobu uniknięcia używania nazw specyficzny dla języka.  
  
## <a name="word-choice"></a>Word Choice  
 **✓ DO** wybrać łatwo odczytać identyfikatora nazwy.  
  
 Na przykład właściwość o nazwie `HorizontalAlignment` jest angielski czytelność niż `AlignmentHorizontal`.  
  
 **✓ DO** Preferuj czytelności za pośrednictwem skrócenia.  
  
 Nazwa właściwości `CanScrollHorizontally` jest lepsze niż `ScrollableX` (zasłoniętej odniesienie do osi x).  
  
 **X DO NOT** użyj podkreślenia, łączniki lub innych znaków innych niż alfanumeryczne.  
  
 **X DO NOT** Użyj notacji Węgierskiej.  
  
 **X AVOID** przy użyciu identyfikatorów, które powodują konflikt z słów kluczowych z powszechnie używane języki programowania.  
  
 Zgodnie z 4 reguły z Common Language Specification (CLS) wszystkie języki zgodne należy podać mechanizm, który umożliwia dostęp do nazwanych elementy, które korzystają odpowiadającej danemu językowi słowa kluczowego jako identyfikatora. C#, na przykład używa znaku jako mechanizm ucieczki w tym przypadku @. Jednak nadal jest dobry pomysł, aby uniknąć typowe słowa kluczowe, ponieważ jest dużo trudniejsze do korzystania z metody przy użyciu sekwencji unikowej niż jeden bez niego.  
  
## <a name="using-abbreviations-and-acronyms"></a>Za pomocą skrótów i akronimów  
 **X DO NOT** Użyj skrótów lub skrótów jako część nazwy identyfikatorów.  
  
 Na przykład użyć `GetWindow` zamiast `GetWin`.  
  
 **X DO NOT** używać żadnych skrótów, które nie są powszechnie zaakceptowany, a nawet wtedy, gdy są one, tylko wtedy, gdy jest to konieczne.  
  
## <a name="avoiding-language-specific-names"></a>Unikanie specyficzny dla języka nazw  
 **✓ DO** użycie nazwy semantycznie interesujące zamiast słowa kluczowe specyficzne dla języka dla nazwy typu.  
  
 Na przykład `GetLength` jest nazwą lepsze niż `GetInt`.  
  
 **✓ DO** Użyj nazwy ogólnej typu CLR, a nie nazwę specyficzne dla języka w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego poza jego typu.  
  
 Na przykład metoda konwersji <xref:System.Int64> powinno się nazywać `ToInt64`, a nie `ToLong` (ponieważ <xref:System.Int64> jest nazwą CLR dla języka C# — określonego aliasu `long`). W poniższej tabeli przedstawiono kilka podstawowych typów danych przy użyciu nazwy typów CLR (a także odpowiednie nazwy typów dla języka C#, Visual Basic i C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**short bez znaku**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64 —**|**__int64 bez znaku**|**UInt64 —**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Boolean**|**bool**|**Boolean**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**Ciąg**|**Ciąg**|**Ciąg**|  
|**object**|**Obiekt**|**Obiekt**|**Obiekt**|  
  
 **✓ DO** Użyj nazwą pospolitą, takiego jak `value` lub `item`, zamiast powtarzające się nazwa typu w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego i typ parametru nie jest ważna.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Nazwy nowych wersji istniejących interfejsów API  
 **✓ DO** Użyj nazwy podobne do starego interfejsu API, podczas tworzenia nowych wersji istniejących interfejsu API.  
  
 Pozwala to wyróżnić relacja między interfejsami API.  
  
 **✓ DO** preferowane jest dodanie sufiksu zamiast prefiksu wskazać nową wersję istniejącego interfejsu API.  
  
 To pomoże odnajdywania, przeglądając dokumentację, lub za pomocą funkcji IntelliSense. Stara wersja interfejsu API zostaną zorganizowane blisko nowe interfejsy API, ponieważ większość przeglądarek i technologii IntelliSense Pokaż identyfikatorów w kolejności alfabetycznej.  
  
 **✓ CONSIDER** przy użyciu całkowicie nowe, ale łatwy do rozpoznania identyfikator, zamiast dodawania sufiks lub prefiks.  
  
 **✓ DO** sufiks numeryczny do wskazania użyć nową wersję istniejącego interfejsu API, szczególnie jeśli istniejącej nazwy interfejsu API jest tylko nazwę, która ma sens (tj., jeśli jest standardem branżowym) i dodawania żadnych zrozumiały sufiks (lub zmiana nazwy) nie jest aplikacji Opcja ropriate.  
  
 **X DO NOT** "Ex" (lub podobny) sufiks identyfikatora odróżniający go od wcześniejszej wersji tego samego interfejsu API.  
  
 **✓ DO** Użyj sufiksu "64", wprowadzając wersje interfejsów API, które działają na 64-bitowa liczba całkowita (długich liczb całkowitych) zamiast 32-bitową liczbę całkowitą. Potrzebujesz takiego podejścia, gdy istnieje istniejących interfejsów API 32-bitowy; nie rób tego na zupełnie nowe interfejsy API w wersji 64-bitowych.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
