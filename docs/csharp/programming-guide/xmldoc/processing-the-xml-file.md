---
title: Przetwarzanie pliku XML (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: b95101d2f8e12f7c6fee5b410e7801f9d890182d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Przetwarzanie pliku XML (Przewodnik programowania w języku C#)
Kompilator generuje ciąg Identyfikatora dla każdego konstrukcji w kodzie zostanie oznaczony do generowania dokumentacji. (Informacje o sposobie tagów w kodzie, zobacz [tagi zalecane dla komentarzy do dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).) Ciąg Identyfikatora unikatowo identyfikuje konstrukcja. Programy, które przetwarzają plik XML można umożliwia zidentyfikowanie odpowiadający mu element .NET Framework metadane/odbicia dotyczy dokumentacji ciąg Identyfikatora.  
  
 Plik XML nie jest hierarchiczną reprezentację kodu; jest płaska lista, która ma identyfikator wygenerowany dla każdego elementu.  
  
 Kompilator stosuje następujące reguły podczas generowania ciągi identyfikatorów:  
  
-   Nie biały znak jest ciąg.  
  
-   Pierwsza część ciąg Identyfikatora określa rodzaj elementu członkowskiego identyfikowalne i jednego znaku z dwukropkiem. Używane są następujące typy elementu członkowskiego:  
  
    |Znak|Opis|  
    |---------------|-----------------|  
    |N|— przestrzeń nazw<br /><br /> Nie można dodać komentarze dokumentacji do przestrzeni nazw, ale możesz wprowadzić cref odwołania do nich, jeśli są obsługiwane.|  
    |T|Typ: klasy, interfejsu, struktury, wyliczenia, delegata|  
    |F|pole|  
    |P|właściwości (łącznie z indeksatorów i inne właściwości indeksowane)|  
    |M|(w tym takie specjalne metody jako konstruktorów, Operatorzy i tak dalej) — metoda|  
    |E|zdarzenie|  
    |!|Ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o tym błędzie. Kompilator języka C# generuje informacje o błędzie dla łącza, które nie zostały rozpoznane.|  
  
-   Druga część ciągu jest w pełni kwalifikowana nazwa elementu, zaczynając od katalogu głównego przestrzeni nazw. Nazwa elementu, jego otaczającego typów i nazw oddzielone kropkami. Jeśli nazwa elementu zawiera okresów, są one zastąpione kratki (#). Zakłada się, że żadne pozycje nie kratki bezpośrednio w swoim imieniu. Na przykład Pełna nazwa konstruktora ciąg będzie "System.String.#ctor".  
  
-   Dla właściwości i metody w przypadku argumentów dla metody, ujęte w nawiasy listy argumentów jest zgodna. Jeśli nie ma żadnych argumentów, nawiasów, nie są dostępne. Argumenty są oddzielone przecinkami. Kodowanie każdy argument następujące bezpośrednio, jak jest zakodowany w podpisie .NET Framework:  
  
    -   Typy podstawowe. Typy regularne (po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowana nazwa typu.  
  
    -   Typy wewnętrzne (na przykład ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. i ELEMENT_TYPE_VOID) są reprezentowane jako w pełni kwalifikowana nazwa typu odpowiadającego pełna. Na przykład System.Int32 lub System.TypedReference.  
  
    -   Poprawności elementu ELEMENT_TYPE_PTR jest reprezentowany jako ' *' następujące zmodyfikowanej typu.  
  
    -   ELEMENT_TYPE_BYREF jest reprezentowany jako "@" następujące zmodyfikowanej typu.  
  
    -   ELEMENT_TYPE_PINNED jest reprezentowany jako "^" następujące zmodyfikowanej typu. Kompilator języka C# nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_CMOD_REQ jest reprezentowany jako "&#124;" i w pełni kwalifikowaną nazwę klasy modyfikator, po modyfikacji typu. Kompilator języka C# nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_CMOD_OPT jest reprezentowany jako "!" i w pełni kwalifikowaną nazwę klasy modyfikator, po modyfikacji typu.  
  
    -   ELEMENT_TYPE_SZARRAY jest reprezentowany jako [następującego typu elementu tablicy "]".  
  
    -   ELEMENT_TYPE_GENERICARRAY jest reprezentowany jako "[?]" następującego typu elementu tablicy. Kompilator języka C# nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_ARRAY jest reprezentowany jako [*ich*:`size`,*ich*:`size`] liczba przecinkami w przypadku rangę - 1 oraz dolną granicę i rozmiar każdego wymiaru, jeśli znane są reprezentowane w dziesiętnych. Jeśli nie określono dolną granicę lub rozmiar, po prostu zostanie pominięty. Jeśli pominięto dolna granica i rozmiaru dla określonego wymiaru ":" zostanie pominięty również. Na przykład 2-wymiarową tablicą o 1 jako nieokreślony rozmiary i dolne granice tablicy to [1:, 1:].  
  
    -   ELEMENT_TYPE_FNPTR jest reprezentowany jako "= FUNC:`type`(*podpisu*)", gdzie `type` jest zwracany typ i *podpisu* jest argumenty metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. Kompilator języka C# nigdy nie generuje to.  
  
     Następujące składniki podpisu nie są reprezentowane, ponieważ nigdy nie są używane dla różnego przeciążonych metod:  
  
    -   Konwencja wywoływania  
  
    -   Zwracany typ  
  
    -   ELEMENT ELEMENT_TYPE_SENTINEL  
  
-   W przypadku konwersji operatory tylko (op_Implicit i op_Explicit), zwracana wartość metody są kodowane jako "~" następuje typ zwracany jako zakodowany powyżej.  
  
-   Dla typów ogólnych Nazwa typu będzie następować wstecz znaczników, a następnie liczbę wskazującą liczbę parametrów typu ogólnego.  Na przykład  
  
     ``<member name="T:SampleClass`2">`` jest znacznik typu, który jest zdefiniowany jako `public class SampleClass<T, U>`.  
  
     Dla metod biorąc typów podstawowych jako parametrów, parametry typu ogólnego są określone jako liczby poprzedzone znakiem Takty Wstecz (na przykład \`0, 1 ").  Każdy liczba reprezentująca liczony od zera tablicy notacji ogólnych parametrów typu.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach pokazano, jak identyfikator ciągi dla klasy i jej elementów członkowskich powinien zostać wygenerowany:  
  
 [!code-csharp[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/processing-the-xml-file_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
