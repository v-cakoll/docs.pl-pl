---
title: Refaktoryzacja do czystych funkcji (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: ed9b33ed2b9669cb4412177086fc648865e4954a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoryzacja do czystych funkcji (C#)

Ważnym aspektem czysty przekształcenia funkcjonalności jest poznanie Refaktoryzuj kodu za pomocą czystych funkcji.  
  
> [!NOTE]
>  Powszechne nazewnictwo w programowanie funkcjonalne jest, że Refaktoryzuj programy przy użyciu czystych funkcji. W języku Visual Basic i C++ to wyrównuje przy użyciu funkcji w odpowiednich języków. Jednak w języku C#, funkcje są wywoływane metody. Na potrzeby tego omówienia czystej funkcji jest implementowany jako metoda w języku C#.  
  
 Jak już wspomniano w tej sekcji, czystej funkcji ma dwie przydatne cechy:  
  
-   Go nie ma skutków ubocznych. Funkcja nie zmienia żadnych zmiennych lub danych dowolnego typu poza funkcję.  
  
-   Jest ona zgodna. Biorąc pod uwagę ten sam zestaw danych wejściowych, zawsze zwróci taką samą wartość w danych wyjściowych.  
  
 Jednym ze sposobów przechodzenia do programowania funkcyjnego jest Refaktoryzuj istniejący kod, aby wyeliminować niepotrzebne efektów ubocznych i zależnościami zewnętrznymi. W ten sposób można utworzyć wersji czystej funkcji istniejącego kodu.  
  
 W tym temacie omówiono jest funkcja czysty i co nie jest. [Samouczek: manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) samouczek przedstawia sposób modyfikowania dokumentu schemat WordprocessingML i zawiera dwa przykłady do refaktoryzacji przy użyciu czystej funkcji.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Wyeliminowanie efektów ubocznych i zależnościami zewnętrznymi  
 Poniższe przykłady kontrastu dwóch funkcji nie jest czysty i czystej funkcji.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Czystej funkcji, która zmienia elementu członkowskiego klasy  
 W poniższym kodzie `HyphenatedConcat` funkcja nie jest czystej funkcji, ponieważ modyfikuje `aMember` element członkowski danych klasy:  
  
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
  
 Zwróć uwagę, że jego nie znaczenia czy dane są modyfikowane ma `public` lub `private` dostępu lub jest `static` elementu członkowskiego lub elementu członkowskiego wystąpienia. Czystej funkcji nie zmienia żadnych danych poza funkcję.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Czystej funkcji, która zmienia argumentu  
 Ponadto następujące wersja tej samej funkcji nie jest czysty ponieważ modyfikuje zawartość jej parametr `sb`.  
  
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
  
 Ta wersja programu daje takie same dane wyjściowe jako pierwszej wersji, ponieważ `HyphenatedConcat` funkcja została zmieniona wartość (stan) jej pierwszy parametr wywołując <xref:System.Text.StringBuilder.Append%2A> funkcję elementu członkowskiego. Należy pamiętać, że ta zmiana występuje mimo fakt który `HyphenatedConcat` używa przekazywanie parametru wywołania przez wartość.  
  
> [!IMPORTANT]
>  Dla typów referencyjnych Jeśli parametr zostanie przekazany przez wartość, jej wynikiem kopię odwołanie do obiektu przekazywany. Ta kopia nadal jest skojarzona z tych samych danych wystąpienia co oryginalny odwołania (do czasu zmienna odwołania jest przypisana do nowego obiektu). Wywołanie przez odwołanie nie jest zawsze wymagane dla funkcji zmodyfikować parametr.  
  
### <a name="pure-function"></a>Czystej funkcji  
To następnej wersji programu pokazano, jak wdrożyć `HyphenatedConcat` działać jako czystej funkcji.  
  
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
  
 Ponownie, ta wersja tworzy w tym samym wierszu danych wyjściowych: `StringOne-StringTwo`. Należy pamiętać, że aby zachować wartości połączonych, jest ona przechowywana w zmiennej pośredniego `s2`.  
  
 Jedno podejście, które mogą być bardzo przydatne jest napisanie funkcje, które są lokalnie oczyścić zanieczyszczony (to, że ich zadeklarować i modyfikowanie zmiennych lokalnych), ale są globalnie czysty. Takie funkcje ma wiele cech możliwości pożądane, ale uniknąć kilku więcej zwichrowanych funkcjonalności idioms programowania, np. konieczności rekursję podczas proste pętli będzie wykonywać samo.  
  
## <a name="standard-query-operators"></a>Standardowe operatory zapytań  
 Istotne cechy standardowych operatorów zapytań jest, że są one zaimplementowane jako czystych funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności Pure (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Programowanie funkcjonalne a Konieczne programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
