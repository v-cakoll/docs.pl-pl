---
title: Ogólne konwencje nazewnictwa
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc54b8bdc96a5038dc75111d9833e70e7ffd2e9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="general-naming-conventions"></a>Ogólne konwencje nazewnictwa
W tej sekcji opisano ogólne konwencji nazewnictwa odnoszą się do wyboru word wskazówki na temat używania skrótów i akronimów i zalecenia dotyczące należy unikać nazw specyficzny dla języka.  
  
## <a name="word-choice"></a>Wybór programu Word  
 **CZY ✓** wybrać łatwo odczytać identyfikatora nazwy.  
  
 Na przykład właściwość o nazwie `HorizontalAlignment` jest angielski czytelność niż `AlignmentHorizontal`.  
  
 **CZY ✓** Preferuj czytelności za pośrednictwem skrócenia.  
  
 Nazwa właściwości `CanScrollHorizontally` jest lepszym rozwiązaniem niż `ScrollableX` (zasłoniętej odwołania do osi x).  
  
 **X nie** użyj podkreślenia, łączniki lub innych znaków innych niż alfanumeryczne.  
  
 **X nie** Użyj notacji Węgierskiej.  
  
 **X należy UNIKAĆ** przy użyciu identyfikatorów, które powodują konflikt z słów kluczowych z powszechnie używane języki programowania.  
  
 Zgodnie z zasady 4 wspólnej specyfikacji języka (CLS) wszystkie języki zgodne podać mechanizm umożliwiający dostęp do nazwanego elementy, które korzystają ze słowem kluczowym tego języka jako identyfikator. C#, na przykład używa znaku jako mechanizmu ucieczki w tym przypadku @. Jednak nadal jest dobrym rozwiązaniem, aby uniknąć typowe słowa kluczowe, ponieważ jest znacznie trudniejsze do metody za pomocą sekwencji unikowej niż jeden bez niego.  
  
## <a name="using-abbreviations-and-acronyms"></a>Za pomocą skrótów i akronimów  
 **X nie** Użyj skrótów lub skrótów jako część nazwy identyfikatorów.  
  
 Na przykład użyć `GetWindow` zamiast `GetWin`.  
  
 **X nie** używać żadnych skrótów, które nie są powszechnie zaakceptowany, a nawet wtedy, gdy są one, tylko wtedy, gdy jest to konieczne.  
  
## <a name="avoiding-language-specific-names"></a>Unikanie specyficzny dla języka nazw  
 **CZY ✓** użycie nazwy semantycznie interesujące zamiast słowa kluczowe specyficzne dla języka dla nazwy typu.  
  
 Na przykład `GetLength` jest nazwą lepszą niż `GetInt`.  
  
 **CZY ✓** Użyj nazwy ogólnej typu CLR, a nie nazwę specyficzne dla języka w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego poza jego typu.  
  
 Na przykład metoda konwertowania na <xref:System.Int64> powinno być nazwanym `ToInt64`, a nie `ToLong` (ponieważ <xref:System.Int64> jest nazwą CLR dla języka C# — określonego aliasu `long`). W poniższej tabeli przedstawiono kilka typów danych podstawowych za pomocą nazwy typu CLR (a także odpowiedniej nazwy typu dla C#, Visual Basic i C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**char bez znaku**|**Byte**|  
|**short**|**krótki**|**short**|**Int16**|  
|**ushort**|**UInt16**|**short bez znaku**|**UInt16**|  
|**int**|**Liczba całkowita**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**długa**|**__int64**|**Int64**|  
|**ulong**|**UInt64 —**|**__int64 bez znaku**|**UInt64 —**|  
|**float**|**Pojedynczy**|**float**|**Pojedynczy**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Boolean**|**bool**|**Boolean**|  
|**char**|**char**|**wchar_t**|**char**|  
|**string**|**Ciąg**|**Ciąg**|**Ciąg**|  
|**object**|**Obiekt**|**Obiekt**|**Obiekt**|  
  
 **CZY ✓** Użyj nazwą pospolitą, takiego jak `value` lub `item`, zamiast powtarzające się nazwa typu w rzadkich przypadkach, gdy identyfikator nie ma znaczenia semantycznego i typ parametru nie jest ważna.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Nazwy nowych wersji istniejących interfejsów API  
 **CZY ✓** Użyj nazwy podobne do starego interfejsu API, podczas tworzenia nowych wersji istniejących interfejsu API.  
  
 Pozwala to Wyróżnij relacji między interfejsów API.  
  
 **CZY ✓** preferowane jest dodanie sufiksu zamiast prefiksu wskazać nową wersję istniejącego interfejsu API.  
  
 Ułatwi to Pomoc odnajdywania, przeglądając dokumentację, lub za pomocą funkcji Intellisense. Stara wersja interfejsu API zostaną zorganizowane bliski nowych interfejsów API, ponieważ większość przeglądarek i Intellisense Pokaż identyfikatorów w kolejności alfabetycznej.  
  
 **ROZWAŻ ✓** przy użyciu całkowicie nowe, ale łatwy do rozpoznania identyfikator, zamiast dodawania sufiks lub prefiks.  
  
 **CZY ✓** sufiks numeryczny do wskazania użyć nową wersję istniejącego interfejsu API, szczególnie jeśli istniejącej nazwy interfejsu API jest tylko nazwę, która ma sens (tj., jeśli jest standardem branżowym) i dodawania żadnych zrozumiały sufiks (lub zmiana nazwy) nie jest aplikacji Opcja ropriate.  
  
 **X nie** "Ex" (lub podobny) sufiks identyfikatora odróżniający go od wcześniejszej wersji tego samego interfejsu API.  
  
 **CZY ✓** Użyj sufiksu "64", wprowadzając wersje interfejsów API, które działają na 64-bitowa liczba całkowita (długich liczb całkowitych) zamiast 32-bitową liczbę całkowitą. Należy o zastosowaniu takiego podejścia, gdy istnieje istniejących API 32-bitowy; nie robi to całkowicie nowe interfejsy API w wersji 64-bitowych.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
