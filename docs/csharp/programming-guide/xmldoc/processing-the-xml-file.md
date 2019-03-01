---
title: Przetwarzanie pliku XML - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1015e5b69f7701f772bc853bba53873fd065a996
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967935"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Przetwarzanie pliku XML (Przewodnik programowania w języku C#)
Kompilator generuje ciąg Identyfikatora dla każdego konstrukcji w kodzie, który jest oznaczony do generowania dokumentacji. (Aby dowiedzieć się, jak oznaczyć swój kod, zobacz [tagi zalecane dla komentarzy do dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).) Ciąg Identyfikatora jednoznacznie identyfikuje konstrukcja. Programy, które przetwarzają pliku XML można umożliwia zidentyfikowanie odpowiadający element metadanych/odbicie .NET Framework dokumentacja dotyczy ciąg Identyfikatora.  
  
 Plik XML jest hierarchiczną reprezentację kodu; jest płaska lista, która ma identyfikator wygenerowany dla każdego elementu.  
  
 Kompilator stosuje następujące reguły podczas generowania ciągi identyfikatorów:  
  
-   Żadne inne białe znajduje się w ciągu.  
  
-   Pierwsza część ciąg Identyfikatora określa rodzaj elementu członkowskiego są identyfikowane za pomocą pojedynczy znak z dwukropkiem. Używane są następujące typy elementu członkowskiego:  
  
    |Znak|Opis|  
    |---------------|-----------------|  
    |N|— przestrzeń nazw<br /><br /> Nie można dodać komentarze dokumentacji do przestrzeni nazw, ale możesz wprowadzać cref odwołania do nich, jeśli są obsługiwane.|  
    |T|Typ: klasy, interfejsu, struktury, wyliczenia, delegat|  
    |F|pole|  
    |P|właściwości (w tym indeksatory lub innych właściwości indeksowane)|  
    |M|metody (w tym specjalnych metodami, takimi jak konstruktory, operatorów i tak dalej)|  
    |E|zdarzenie|  
    |!|Ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o tym błędzie. Kompilator języka C# generuje informacje o błędzie dla łączy, których nie można rozpoznać.|  
  
-   Druga część ciągu jest w pełni kwalifikowana nazwa elementu, począwszy od głównego obszaru nazw. Nazwa elementu, jego otaczającego typów i przestrzeni nazw są oddzielone kropkami. Jeśli nazwa elementu zawiera kropek, są one zastąpione przez znak kratki (#). Zakłada się, że żaden element ma znak kratki bezpośrednio w jego nazwę. Na przykład w pełni kwalifikowaną nazwę Konstruktor ciąg będzie "System.String.#ctor".  
  
-   Dla właściwości i metod w przypadku argumentów dla metody, na liście argumentów w nawiasach jest zgodna. Jeśli nie ma żadnych argumentów, nawiasy nie są obecne. Argumenty są oddzielone przecinkami. Kodowanie każdego argumentu następuje bezpośrednio, jak jest zakodowany w podpisie .NET Framework:  
  
    -   Typy podstawowe. Regularne typów (ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowaną nazwę typu.  
  
    -   Typy wewnętrzne (na przykład ELEMENT_TYPE_I4 ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. i ELEMENT_TYPE_VOID) są reprezentowane jako w pełni kwalifikowaną nazwę odpowiedniego typu pełna. Na przykład System.Int32 lub System.TypedReference.  
  
    -   ELEMENT_TYPE_PTR jest reprezentowany jako "\*" po modyfikacji typu.  
  
    -   Pole jest reprezentowany jako "\@" po modyfikacji typu.  
  
    -   ELEMENT_TYPE_PINNED jest reprezentowany jako "^" po modyfikacji typu. Kompilator języka C# nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_CMOD_REQ jest reprezentowany jako "&#124;" i w pełni kwalifikowaną nazwę klasy modyfikator, zmodyfikowany typ następujące. Kompilator języka C# nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_CMOD_OPT jest reprezentowany jako "!" i w pełni kwalifikowaną nazwę klasy modyfikator, zmodyfikowany typ następujące.  
  
    -   ELEMENT_TYPE_SZARRAY jest reprezentowany jako "[]", zgodnie z typem elementu tablicy.  
  
    -   ELEMENT_TYPE_GENERICARRAY jest reprezentowany jako "[?]" po typ elementu tablicy. Kompilator języka C# nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_ARRAY jest reprezentowany jako [*ich*:`size`,*ich*:`size`] gdzie liczba przecinków jest ranga - 1 i dolne granice i rozmiaru każdego wymiaru, jeśli znane są reprezentowane w zapisie dziesiętnym. Jeśli dolna granica lub rozmiar nie zostanie określony, po prostu zostanie pominięta. W przypadku pominięcia dolną granicę i rozmiar dla określonego wymiaru ":" pominięto w także. Na przykład, to 2-wymiarowej tablicy przy użyciu 1 jako nieokreślony rozmiary i dolne granice [1:, 1:].  
  
    -   ELEMENT_TYPE_FNPTR jest reprezentowany jako "= FUNC:`type`(*podpisu*)", gdzie `type` jest zwracany typ i *podpisu* jest argumenty metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. Kompilator języka C# nigdy nie generuje to.  
  
     Następujące składniki podpis nie są reprezentowane, ponieważ nigdy nie są one używane do różnicujący przeciążonych metod:  
  
    -   Konwencja wywoływania  
  
    -   Zwracany typ  
  
    -   ELEMENT_TYPE_SENTINEL  
  
-   Konwersja operatory tylko (op_implicit — i op_explicit —), zwracana wartość metody jest zakodowane jako "~" następuje typ zwracany jako kodowaniem powyżej.  
  
-   Dla typów ogólnych Nazwa typu następuje początkowych, a następnie na liczbę wskazującą liczbę parametrów typu genetycznego. Na przykład:
  
     ``<member name="T:SampleClass`2">`` to znacznik typu, który jest zdefiniowany jako `public class SampleClass<T, U>`.  
  
     Dla metod biorąc typów podstawowych jako parametrów, parametry typu ogólnego są określane jako cyfry poprzedzony ująć w znaki grawisu (na przykład \`0,\`1). Liczba, każda reprezentująca notacji tablicę indeksowaną od zera dla ogólnych parametrów typu.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach pokazano, jak identyfikator ciągi dla klasy i zostanie wygenerowany, jego członków:  
  
 [!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
