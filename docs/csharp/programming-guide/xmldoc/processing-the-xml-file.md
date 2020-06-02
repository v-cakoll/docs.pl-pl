---
title: Przetwarzanie pliku XML — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1e3d96f9398f2c08ed715111f01987e2d1948439
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287262"
---
# <a name="process-the-xml-file-c-programming-guide"></a>Przetwarzanie pliku XML (Przewodnik programowania w języku C#)

Kompilator generuje ciąg identyfikatora dla każdej konstrukcji w kodzie, który jest oznaczony do generowania dokumentacji. (Aby uzyskać informacje na temat znakowania kodu, zobacz [zalecane Tagi dla komentarzy do dokumentacji](./recommended-tags-for-documentation-comments.md)). Ciąg identyfikatora jednoznacznie identyfikuje konstrukcję. Programy, które przetwarzają plik XML, mogą używać ciągu identyfikatora do identyfikowania odpowiednich metadanych lub elementów odbicia platformy .NET, do których odnosi się dokumentacja.

## <a name="id-strings"></a>Ciągi identyfikatorów

Plik XML nie jest hierarchiczną reprezentacją kodu. Jest to płaska lista, która ma wygenerowany identyfikator dla każdego elementu.

Podczas generowania ciągów identyfikatorów kompilator przestrzega następujących reguł:

- Brak białego znaku w ciągu.

- Pierwsza część ciągu identyfikuje rodzaj składowej przy użyciu pojedynczego znaku, po którym następuje dwukropek. Używane są następujące typy elementów członkowskich:

    |Znak|Typ elementu członkowskiego|Uwagi|
    |---------------|-----------------|-|
    |N|namespace|Nie można dodać komentarzy do dokumentacji do przestrzeni nazw, ale możesz wprowadzić do nich odwołania cref, jeśli są obsługiwane.|
    |T|typ|Typ może być klasą, interfejsem, strukturą, wyliczeniem lub delegatem.|
    |F|pole|
    |P|property|Obejmuje indeksatory lub inne właściwości indeksowane.|
    |M|method|Obejmuje metody specjalne, takie jak konstruktory i operatory.|
    |E|event|
    |!|ciąg błędu|Pozostała część ciągu zawiera informacje o błędzie. Kompilator języka C# generuje informacje o błędzie dla linków, których nie można rozpoznać.|

- Druga część ciągu to w pełni kwalifikowana nazwa elementu, rozpoczynając od elementu głównego przestrzeni nazw. Nazwa elementu, jego typy otaczające i przestrzeń nazw są oddzielone kropkami. Jeśli nazwa samego elementu ma okresy, są one zastępowane przez znak hash ("#"). Przyjęto założenie, że żaden element nie ma znaku skrótu bezpośrednio w nazwie. Na przykład w pełni kwalifikowana nazwa konstruktora String to "System. String. #ctor".

- W przypadku właściwości i metod lista parametrów ujęta w nawiasy. Jeśli nie ma żadnych parametrów, nie ma nawiasów. Parametry są rozdzielone przecinkami. Kodowanie każdego parametru następuje bezpośrednio w postaci, w jakiej jest zakodowany w podpisie .NET:

  - Typy podstawowe. Zwykłe typy (ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowana nazwa typu.

  - Typy wewnętrzne (na przykład ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF i ELEMENT_TYPE_VOID) są reprezentowane jako w pełni kwalifikowana nazwa odpowiedniego pełnego typu. Na przykład system. Int32 lub system. TypedReference.

  - ELEMENT_TYPE_PTR jest reprezentowane jako " \* " po zmodyfikowanym typie.

  - ELEMENT_TYPE_BYREF jest reprezentowane jako " \@ " po zmodyfikowanym typie.

  - ELEMENT_TYPE_PINNED jest reprezentowane jako "^" po zmodyfikowanym typie. Kompilator języka C# nigdy nie generuje tego.

  - ELEMENT_TYPE_CMOD_REQ jest reprezentowane jako "&#124;" i w pełni kwalifikowana nazwa klasy modyfikującej, po zmodyfikowanym typie. Kompilator języka C# nigdy nie generuje tego.

  - ELEMENT_TYPE_CMOD_OPT jest reprezentowane jako "!" i w pełni kwalifikowana nazwa klasy modyfikującej, po zmodyfikowanym typie.

  - ELEMENT_TYPE_SZARRAY jest reprezentowane jako "[]" po typie elementu tablicy.

  - ELEMENT_TYPE_GENERICARRAY jest reprezentowane jako "[?]" po typie elementu tablicy. Kompilator języka C# nigdy nie generuje tego.

  - ELEMENT_TYPE_ARRAY jest reprezentowane jako [*lowerbound*: `size` ,*lowerbound*: `size` ], gdzie liczba przecinków jest rangą 1, a dolne granice i rozmiar każdego wymiaru, jeśli są znane, są reprezentowane w postaci dziesiętnej. Jeśli Dolna granica nie zostanie określona, zostanie pominięta. Jeśli Dolna granica i rozmiar określonego wymiaru zostaną pominięte, znak ":" również zostanie pominięty. Na przykład tablica 2-wymiarową z 1 jako dolne granice i nieokreślone rozmiary to [1:, 1:].

  - ELEMENT_TYPE_FNPTR jest reprezentowana jako "= FUNC: `type` (*Signature*)", gdzie `type` jest typem zwracanym, a *Signature* to argumenty metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. Kompilator języka C# nigdy nie generuje tego.

  Poniższe składniki podpisu nie są reprezentowane, ponieważ nie są używane do odróżniania przeciążonych metod:

  - Konwencja wywoływania

  - Typ zwracany

  - ELEMENT_TYPE_SENTINEL

- W przypadku operatorów konwersji ( `op_Implicit` i `op_Explicit` ) wartość zwracana metody jest zaszyfrowana jako "~", po której następuje zwracany typ.

- W przypadku typów ogólnych, nazwa typu następuje przez nieskończoność, a następnie liczbę, która wskazuje liczbę parametrów typu ogólnego. Na przykład:

     ``<member name="T:SampleClass`2">``jest tagiem dla typu, który jest zdefiniowany jako `public class SampleClass<T, U>` .

     W przypadku metod, które przyjmują typy ogólne jako parametry, parametry typu ogólnego są określone jako liczby poprzedzone znakami kreskowych (na przykład \` 0, \` 1). Każda liczba reprezentuje notację tablicową opartą na zero dla ogólnych parametrów typu.

## <a name="examples"></a>Przykłady

W poniższych przykładach pokazano, jak generowane są ciągi identyfikatorów dla klasy i jej członków:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (opcje kompilatora C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
