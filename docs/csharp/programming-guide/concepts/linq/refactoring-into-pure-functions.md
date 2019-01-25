---
title: Refaktoryzacja do czystych funkcji (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 3e856c1e32d4b0dc16291e1b913e9a5cc19717c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497134"
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoryzacja do czystych funkcji (C#)

Ważnym aspektem czystych przekształceń funkcjonalnych jest nauki refaktoryzacji kodu przy użyciu czystej funkcji.  
  
> [!NOTE]
>  Powszechne nazewnictwo w programowania funkcjonalnego jest Refaktoryzacja programach przy użyciu czystych funkcji. W języku Visual Basic i C++ to zgodne z korzystania z funkcji w odpowiednich języków. Jednak w języku C#, funkcje są wywoływane metody. Dla celów tej dyskusji czystej funkcji jest wdrażany jako metoda w języku C#.  
  
 Jak wspomniano wcześniej w tej sekcji, czystej funkcji ma dwie właściwości przydatne:  
  
-   Nie ma żadnych efektów ubocznych. Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu spoza tej funkcji.  
  
-   Jest ona zgodna. Biorąc pod uwagę ten sam zestaw danych wejściowych, która zawsze zwraca tę samą wartość w danych wyjściowych.  
  
 Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Przeprowadź refaktoryzację istniejącego kodu, aby wyeliminować niepotrzebne efekty uboczne i zależności zewnętrznych. W ten sposób można utworzyć wersji czystą funkcję istniejącego kodu.  
  
 W tym temacie omówiono funkcja czystego jest i co nie jest. [Samouczka: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu WordprocessingML i zawiera dwa przykłady jak Refaktoryzacja, przy użyciu czystej funkcji.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminując skutki uboczne i zależności zewnętrznych  
 Poniższe przykłady porównać dwie funkcje — czyste i czystą funkcję.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Czystej funkcji, która zmienia składowej klasy  
 W poniższym kodzie `HyphenatedConcat` funkcja nie jest funkcją czystego, ponieważ modyfikuje `aMember` element członkowski danych w klasie:  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HyphenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HyphenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
StringOne-StringTwo  
```  
  
 Zwróć uwagę, że jej nie ma znaczenia tego, czy ma modyfikacji danych `public` lub `private` dostępu lub jest `static` elementu członkowskiego lub elementu członkowskiego wystąpienia. Czystą funkcję nie zmienia żadnych danych poza funkcją.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Czystej funkcji, która zmienia argumentu  
 Ponadto, następująca wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jako parametr `sb`.  
  
```csharp  
public class Program  
{  
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HyphenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 Ta wersja programu daje takie same dane wyjściowe jako pierwsza wersja, ponieważ `HyphenatedConcat` funkcja została zmieniona wartość (stan) jako pierwszy parametr, wywołując <xref:System.Text.StringBuilder.Append%2A> funkcja elementu członkowskiego. Uwaga występowanie tej zmiany, pomimo faktu, `HyphenatedConcat` używa wywołań przez wartość parametru przekazywania.  
  
> [!IMPORTANT]
>  Dla typów odwołań w przypadku przekazania parametr przez wartość, jej powoduje kopię odwołanie do obiektu przekazywana. Ta kopia jest nadal skojarzone z tymi samymi danymi wystąpienia jako odwołanie do oryginalnego (aż do zmiennej odwołania jest przypisany do nowego obiektu). Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.  
  
### <a name="pure-function"></a>Czystej funkcji  
Ta następnej wersji programu przedstawia sposób implementowania `HyphenatedConcat` pełnią czystą funkcję.  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 Ponownie generuje ten sam wiersz danych wyjściowych w tej wersji: `StringOne-StringTwo`. Należy pamiętać, aby zachować wartość połączone, jest on przechowywany w zmiennej pośrednich `s2`.  
  
 Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (oznacza to, mogą zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty. Takie funkcje, ma wiele cech pożądane możliwości tworzenia, ale uniknąć niektórych bardziej zawiłe funkcjonalności idiomy programowania, takich jak konieczności rekursję, gdy prostej pętli może osiągnąć to samo.  
  
## <a name="standard-query-operators"></a>Standardowe operatory zapytań  
 Ważną cechą standardowych operatorów zapytań jest, że są implementowane jako czystych funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych przekształceń funkcjonalnych (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a Programowanie imperatywne (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
