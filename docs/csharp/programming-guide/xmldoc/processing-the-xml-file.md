---
title: Przetwarzanie pliku XML — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: b2b19a2b2c46df5b78b6ebba48955cae55d32121
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846933"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Przetwarzanie pliku XML (Przewodnik programowania w języku C#)

Kompilator generuje ciąg identyfikatora dla każdej konstrukcji w kodzie, który jest oznaczony do generowania dokumentacji. (Aby uzyskać informacje na temat znakowania kodu, zobacz [zalecane Tagi dla komentarzy do dokumentacji](./recommended-tags-for-documentation-comments.md)). Ciąg identyfikatora jednoznacznie identyfikuje konstrukcję. Programy, które przetwarzają plik XML, mogą używać ciągu identyfikatora do identyfikowania odpowiednich .NET Framework metadanych/elementu odbicia, do których odnosi się dokumentacja.

Plik XML nie jest hierarchiczną reprezentacją kodu; jest to płaska lista, która ma wygenerowany identyfikator dla każdego elementu.

Podczas generowania ciągów identyfikatorów kompilator przestrzega następujących reguł:

- Brak białego znaku w ciągu.

- Pierwsza część ciągu identyfikatora identyfikuje rodzaj identyfikowanego elementu członkowskiego za pomocą pojedynczego znaku, po którym następuje dwukropek. Używane są następujące typy elementów członkowskich:

    |Znak|Opis|
    |---------------|-----------------|
    |N|— przestrzeń nazw<br /><br /> Nie można dodać komentarzy do dokumentacji do przestrzeni nazw, ale możesz wprowadzić do nich odwołania cref, jeśli są obsługiwane.|
    |T|Typ: Klasa, interfejs, struktura, Wyliczenie, delegat|
    |F|pole|
    |P|Właściwość (w tym indeksatory lub inne właściwości indeksowane)|
    |M|Metoda (łącznie z takimi metodami specjalnymi jak konstruktory, operatory itd.)|
    |E|zdarzenie|
    |!|ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o błędzie. C# Kompilator generuje informacje o błędzie dla linków, których nie można rozpoznać.|

- Druga część ciągu to w pełni kwalifikowana nazwa elementu, rozpoczynając od elementu głównego przestrzeni nazw. Nazwa elementu, jego typy otaczające i przestrzeń nazw są oddzielone kropkami. Jeśli nazwa samego elementu ma okresy, są one zastępowane przez znak hash ("#"). Przyjęto założenie, że żaden element nie ma znaku skrótu bezpośrednio w nazwie. Na przykład w pełni kwalifikowana nazwa konstruktora String byłaby "System. String. #ctor".

- W przypadku właściwości i metod, jeśli istnieją argumenty metody, lista argumentów ujęta w nawiasy. Jeśli nie ma żadnych argumentów, nie ma nawiasów. Argumenty są rozdzielone przecinkami. Kodowanie każdego argumentu następuje bezpośrednio po zakodowaniu w sygnaturze .NET Framework:

  - Typy podstawowe. Zwykłe typy (ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowana nazwa typu.

  - Typy wewnętrzne (na przykład ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF i ELEMENT_TYPE_VOID) są reprezentowane jako w pełni kwalifikowana nazwa odpowiedniego pełnego typu. Na przykład system. Int32 lub system. TypedReference.

  - ELEMENT_TYPE_PTR jest reprezentowany jako "\*" po zmodyfikowanym typie.

  - ELEMENT_TYPE_BYREF jest reprezentowany jako "\@" po zmodyfikowanym typie.

  - ELEMENT_TYPE_PINNED jest reprezentowany jako "^" po zmodyfikowanym typie. C# Kompilator nigdy nie generuje tego.

  - ELEMENT_TYPE_CMOD_REQ jest reprezentowane jako "&#124;" i w pełni kwalifikowana nazwa klasy modyfikującej, po zmodyfikowanym typie. C# Kompilator nigdy nie generuje tego.

  - ELEMENT_TYPE_CMOD_OPT jest reprezentowane jako "!" i w pełni kwalifikowana nazwa klasy modyfikującej, po zmodyfikowanym typie.

  - ELEMENT_TYPE_SZARRAY jest reprezentowane jako "[]" po typie elementu tablicy.

  - ELEMENT_TYPE_GENERICARRAY jest reprezentowane jako "[?]" po typie elementu tablicy. C# Kompilator nigdy nie generuje tego.

  - ELEMENT_TYPE_ARRAY jest reprezentowane jako [*lowerbound*:`size`,*lowerbound*:`size`], gdzie liczba przecinków jest rangą 1, a dolne granice i rozmiar każdego wymiaru, jeśli są znane, są reprezentowane w postaci dziesiętnej. Jeśli Dolna granica nie zostanie określona, zostanie ona po prostu pominięta. Jeśli Dolna granica i rozmiar określonego wymiaru zostaną pominięte, znak ":" również zostanie pominięty. Na przykład tablica 2-wymiarową z 1 jako dolne granice i nieokreślone rozmiary to [1:, 1:].

  - ELEMENT_TYPE_FNPTR jest reprezentowane jako "= FUNC:`type`(*Signature*)", gdzie `type` jest typem zwracanym, a *Signature* jest argumentami metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. C# Kompilator nigdy nie generuje tego.

    Następujące składniki podpisu nie są reprezentowane, ponieważ nie są nigdy używane do odróżniania przeciążonych metod:

  - Konwencja wywoływania

  - Typ zwracany

  - ELEMENT_TYPE_SENTINEL

- W przypadku operatorów konwersji (op_Implicit i op_Explicit) wartość zwracana metody jest zaszyfrowana jako "~", po której następuje zwracany typ, jak powyżej.

- W przypadku typów ogólnych, nazwa typu następuje przez nieskończoność, a następnie liczbę, która wskazuje liczbę parametrów typu ogólnego. Na przykład:

     ``<member name="T:SampleClass`2">`` jest tagiem dla typu, który jest zdefiniowany jako `public class SampleClass<T, U>`.

     W przypadku metod, które pobierają typy ogólne jako parametry, parametry typu generycznego są określone jako liczby poprzedzone znakami kreskowych (na przykład \`0, \`1). Każda liczba reprezentująca notację tablicową opartą na zero dla ogólnych parametrów typu.

## <a name="examples"></a>Przykłady

W poniższych przykładach pokazano, jak generowane są ciągi identyfikatorów dla klasy i jej członków:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (C# opcje kompilatora)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
