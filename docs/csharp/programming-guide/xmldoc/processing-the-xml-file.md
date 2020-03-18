---
title: Przetwarzanie pliku XML — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: bc72cade9ce6edddb88d741a3424405bba0a7ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793395"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Przetwarzanie pliku XML (przewodnik programowania C#)

Kompilator generuje ciąg identyfikatora dla każdej konstrukcji w kodzie, który jest oznaczony do generowania dokumentacji. (Aby uzyskać informacje dotyczące oznaczania kodu, zobacz [Zalecane tagi dla komentarzy do dokumentacji](./recommended-tags-for-documentation-comments.md).) Ciąg identyfikatora jednoznacznie identyfikuje konstrukcję. Programy przetwarzająplik XML można użyć ciągu identyfikatora do zidentyfikowania odpowiedniego elementu metadanych/odbicia .NET Framework, którego dotyczy dokumentacja.

Plik XML nie jest hierarchiczną reprezentacją kodu; jest to płaska lista, która ma wygenerowany identyfikator dla każdego elementu.

Kompilator przestrzega następujących reguł podczas generowania ciągów identyfikatora:

- Żaden biały znak nie jest w ciągu.

- Pierwsza część ciągu Identyfikatoridentyfikuje rodzaj elementu członkowskiego identyfikowanego, za pomocą pojedynczego znaku, po którym następuje dwukropek. Używane są następujące typy elementów członkowskich:

    |Znak|Opis|
    |---------------|-----------------|
    |Nie|przestrzeń nazw<br /><br /> Nie można dodawać komentarzy dokumentacji do obszaru nazw, ale można do nich odwołać cref, gdzie jest to obsługiwane.|
    |T|typ: klasa, interfejs, struktura, wyliczenie lub pełnomocnik|
    |F|pole|
    |P|(w tym indeksatory lub inne właściwości indeksowane)|
    |M|metoda (w tym takie specjalne metody jak konstruktorzy, operatorzy itd.)|
    |E|event|
    |!|ciąg błędu<br /><br /> Reszta ciągu zawiera informacje o błędzie. Kompilator Języka C# generuje informacje o błędach dla łączy, których nie można rozwiązać.|

- Druga część ciągu jest w pełni kwalifikowaną nazwą elementu, zaczynając od katalogu głównego obszaru nazw. Nazwa elementu, jego otaczające typy i obszar nazw są oddzielone kropkami. Jeśli nazwa samego elementu ma kropki, są one zastępowane znakiem skrótu ('#'). Zakłada się, że żaden element nie ma znaku skrótu bezpośrednio w jego nazwie. Na przykład w pełni kwalifikowana nazwa konstruktora String będzie "System.String.#ctor".

- W przypadku właściwości i metod, jeśli istnieją argumenty do metody, lista argumentów ujęta w nawiasy następuje. Jeśli nie ma żadnych argumentów, nie są dostępne żadne nawiasy. Argumenty są oddzielone przecinkami. Kodowanie każdego argumentu następuje bezpośrednio, jak jest zakodowany w podpisie .NET Framework:

  - Typy podstawowe. Regularne typy (ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowana nazwa typu.

  - Typy wewnętrzne (na przykład ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF i ELEMENT_TYPE_VOID) są reprezentowane jako w pełni kwalifikowana nazwa odpowiedniego pełnego typu. Na przykład System.Int32 lub System.TypedReference.

  - ELEMENT_TYPE_PTR jest reprezentowana\*jako ' po zmodyfikowanym typie.

  - ELEMENT_TYPE_BYREF jest reprezentowany jako\@' po zmodyfikowanym typie.

  - ELEMENT_TYPE_PINNED jest reprezentowana jako "^" po zmodyfikowanym typie. Kompilator Języka C# nigdy tego nie generuje.

  - ELEMENT_TYPE_CMOD_REQ jest reprezentowana jako "&#124;" i w pełni kwalifikowaną nazwę klasy modyfikatora, po zmodyfikowanym typie. Kompilator Języka C# nigdy tego nie generuje.

  - ELEMENT_TYPE_CMOD_OPT jest reprezentowana jako "!" i w pełni kwalifikowana nazwa klasy modyfikatora, po zmodyfikowanym typie.

  - ELEMENT_TYPE_SZARRAY jest reprezentowana jako "[]" po typie elementu tablicy.

  - ELEMENT_TYPE_GENERICARRAY jest reprezentowana jako "[?]" po typie elementu tablicy. Kompilator Języka C# nigdy tego nie generuje.

  - ELEMENT_TYPE_ARRAY jest reprezentowana jako`size`[*dolna granica*: ,*dolna granica*:`size`], gdzie liczba przecinków jest rangą - 1, a dolne granice i rozmiar każdego wymiaru, jeśli są znane, są reprezentowane po przecinku. Jeśli dolna granica lub rozmiar nie jest określony, jest po prostu pominięty. Jeśli dolna granica i rozmiar dla określonego wymiaru zostaną pominięte, pominięto również ":". Na przykład tablica dwuwymiarowa z 1 jako dolna granica i nieokreślone rozmiary to [1:,1:].

  - ELEMENT_TYPE_FNPTR jest reprezentowany jako`type`"=FUNC: (*podpis*)", gdzie `type` jest typem zwracanym, a *podpis* jest argumentami metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. Kompilator Języka C# nigdy tego nie generuje.

    Następujące składniki podpisu nie są reprezentowane, ponieważ nigdy nie są używane do różnicowania przeciążonych metod:

  - konwencja wywoływania

  - typ zwracany

  - ELEMENT_TYPE_SENTINEL

- Tylko dla operatorów konwersji (op_Implicit i op_Explicit) wartość zwracana metody jest kodowana jako "~", po której następuje typ zwracany, jak zakodowato powyżej.

- W przypadku typów ogólnych po nazwie typu następuje backtick, a następnie liczba wskazująca liczbę parametrów typu ogólnego. Przykład:

     ``<member name="T:SampleClass`2">``jest tagiem typu zdefiniowanego jako `public class SampleClass<T, U>`.

     W przypadku metod przyjmujących typy ogólne jako parametry, parametry typu ogólnego są określane \`jako\`liczby poprzedzone backtickami (na przykład 0, 1). Każda liczba reprezentująca tablicę o zerowej tablicy dla parametrów ogólnych typu.

## <a name="examples"></a>Przykłady

W poniższych przykładach przedstawiono sposób generowania ciągów identyfikatorów dla klasy i jej elementów członkowskich:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (opcje kompilatora C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
