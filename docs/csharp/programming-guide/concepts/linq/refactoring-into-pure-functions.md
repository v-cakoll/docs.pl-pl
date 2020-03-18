---
title: Refaktoryzacja do czystych funkcji (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253109"
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoryzacja do czystych funkcji (C#)

Ważnym aspektem czystej transformacji funkcjonalnych jest uczenie się refaktoryzacji kodu przy użyciu czystych funkcji.  
  
> [!NOTE]
> Powszechną nomenklaturą w programowaniu funkcjonalnym jest to, że refaktoryzujesz programy przy użyciu czystych funkcji. W językach Visual Basic i C++ jest to zgodne z użyciem funkcji w odpowiednich językach. Jednak w języku C#, funkcje są nazywane metodami. Na potrzeby tej dyskusji czysta funkcja jest implementowana jako metoda w języku C#.  
  
 Jak wspomniano wcześniej w tej sekcji, czysta funkcja ma dwie użyteczne cechy:  
  
- Nie ma skutków ubocznych. Funkcja nie zmienia żadnych zmiennych ani danych dowolnego typu poza funkcją.  
  
- Jest spójny. Biorąc pod uwagę ten sam zestaw danych wejściowych, zawsze będzie zwracać tę samą wartość danych wyjściowych.  
  
 Jednym ze sposobów przejścia do programowania funkcjonalnego jest refaktoryzacji istniejącego kodu w celu wyeliminowania niepotrzebnych skutków ubocznych i zależności zewnętrznych. W ten sposób można utworzyć czyste wersje funkcji istniejącego kodu.  
  
 W tym temacie omówiono, czym jest czysta funkcja, a czym nie. [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) samouczek pokazuje, jak manipulować dokumentem WordprocessingML i zawiera dwa przykłady refaktoryzacji przy użyciu czystej funkcji.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminowanie skutków ubocznych i zależności zewnętrznych  
 Poniższe przykłady kontrastują dwie funkcje nieczyste i czystą funkcję.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Funkcja nieczysta, która zmienia element członkowski klasy  
 W poniższym kodzie `HyphenatedConcat` funkcja nie jest czystą funkcją, `aMember` ponieważ modyfikuje element członkowski danych w klasie:  
  
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
  
```output  
StringOne-StringTwo  
```  
  
 Należy zauważyć, że nie ma `public` znaczenia, czy modyfikowane dane ma lub `private` dostępu, lub jest członkiem `static` członkowskim lub elementem członkowskim wystąpienia. Czysta funkcja nie zmienia żadnych danych poza funkcją.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Funkcja nieczysta, która zmienia argument  
 Ponadto, następująca wersja tej samej funkcji nie jest czysta, ponieważ modyfikuje zawartość jej parametru, `sb`.  
  
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
  
 Ta wersja programu generuje takie same dane wyjściowe jak `HyphenatedConcat` pierwsza wersja, ponieważ funkcja zmieniła wartość (stan) swojego pierwszego parametru, wywołując funkcję elementu członkowskiego. <xref:System.Text.StringBuilder.Append%2A> Należy zauważyć, że ta zmiana `HyphenatedConcat` występuje pomimo tego, że używa przekazywanie parametru wywołania według wartości.  
  
> [!IMPORTANT]
> Dla typów odwołań, jeśli przekażesz parametr według wartości, powoduje to kopię odwołania do obiektu przekazywane. Ta kopia jest nadal skojarzona z tymi samymi danymi wystąpienia co oryginalne odwołanie (dopóki zmienna referencyjna nie zostanie przypisana do nowego obiektu). Odwołanie nie musi być wymagane, aby funkcja zmodyfikowała parametr.  
  
### <a name="pure-function"></a>Czysta funkcja  
Ta następna wersja programu pokazuje, `HyphenatedConcat` jak zaimplementować funkcję jako czystą funkcję.  
  
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
  
 Ponownie, ta wersja daje ten sam `StringOne-StringTwo`wiersz danych wyjściowych: . Należy zauważyć, że aby zachować połączoną wartość, `s2`jest ona przechowywana w zmiennej pośredniej .  
  
 Jednym z podejść, które mogą być bardzo przydatne jest pisanie funkcji, które są lokalnie nieczyste (oznacza to, że deklarują i modyfikują zmienne lokalne), ale są globalnie czyste. Takie funkcje mają wiele pożądanych cech komposability, ale uniknąć niektórych bardziej zawiłe funkcjonalne idiomy programowania, takich jak konieczności korzystania z rekursji, gdy prosta pętla będzie osiągnąć to samo.  
  
## <a name="standard-query-operators"></a>Standardowe operatory zapytań  
 Ważną cechą standardowych operatorów zapytań jest to, że są one implementowane jako czyste funkcje.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przemian funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a programowanie imperatywne (C#)](./functional-programming-vs-imperative-programming.md)
