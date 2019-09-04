---
title: Refaktoryzacja do czystych funkcji (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253109"
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoryzacja do czystych funkcji (C#)

Ważnym aspektem czystych transformacji funkcjonalnych jest uczenie się, jak kod refaktoryzacji przy użyciu czystych funkcji.  
  
> [!NOTE]
> Wspólna Nomenklatura w programowaniu funkcjonalnym polega na tym, że programy refaktoryzacji używają czystych funkcji. W Visual Basic i C++, jest to zgodne z użyciem funkcji w odpowiednich językach. Jednak w programie C#funkcje są nazywane metodami. Na potrzeby tej dyskusji czysta funkcja jest implementowana jako metoda w C#.  
  
 Jak wspomniano wcześniej w tej sekcji, czysta funkcja ma dwie przydatne cechy:  
  
- Nie ma żadnych efektów ubocznych. Funkcja nie zmienia żadnych zmiennych ani danych dowolnego typu poza funkcją.  
  
- Jest ona spójna. Mając ten sam zestaw danych wejściowych, zawsze zwróci tę samą wartość wyjściową.  
  
 Jednym ze sposobów przejścia do programowania funkcjonalnego jest Refaktoryzacja istniejącego kodu w celu wyeliminowania zbędnych efektów ubocznych i zewnętrznych zależności. W ten sposób można utworzyć czystą wersję funkcji istniejącego kodu.  
  
 W tym temacie omówiono czystą funkcję i jej znaczenie. [Samouczek: Manipulowanie zawartością w samouczku WordprocessingML DocumentC#(](./shape-of-wordprocessingml-documents.md) ) pokazuje, jak manipulować dokumentem WordprocessingML i zawiera dwa przykłady sposobu refaktoryzacji przy użyciu czystej funkcji.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Eliminowanie efektów ubocznych i zależności zewnętrznych  
 Poniższe przykłady różnią się dwoma nieczystymi funkcjami i czystą funkcją.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Nieczysta funkcja, która zmienia element członkowski klasy  
 W poniższym kodzie `HyphenatedConcat` funkcja nie jest czystą funkcją, ponieważ `aMember` modyfikuje element członkowski danych w klasie:  
  
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
  
 Należy zauważyć, że nie ma znaczenia, czy modyfikowane `public` dane `private` mają `static` dostęp, czy też jest członkiem lub wystąpieniem. Czysta funkcja nie zmienia żadnych danych poza funkcją.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Nieczysta funkcja, która zmienia argument  
 Ponadto następująca wersja tej samej funkcji nie jest czysta, ponieważ modyfikuje zawartość jej parametru, `sb`.  
  
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
  
 Ta wersja programu daje te same dane wyjściowe co pierwsza wersja, ponieważ `HyphenatedConcat` funkcja zmieniła wartość (stan) pierwszego parametru przez <xref:System.Text.StringBuilder.Append%2A> wywołanie funkcji członkowskiej. Należy zauważyć, że ta zmiana występuje pomimo tego `HyphenatedConcat` faktu, który używa przekazywania parametrów wywołania przez wartość.  
  
> [!IMPORTANT]
> W przypadku typów referencyjnych, Jeśli przekażesz parametr według wartości, wynikiem jest kopia odwołania do obiektu, który jest przekazywany. Ta kopia jest nadal skojarzona z tymi samymi danymi wystąpienia co oryginalne odwołanie (do momentu przypisania zmiennej odniesienia do nowego obiektu). Wywołanie przez odwołanie nie musi być wymagane do zmodyfikowania parametru przez funkcję.  
  
### <a name="pure-function"></a>Czysta funkcja  
Ta Następna wersja programu pokazuje, jak zaimplementować `HyphenatedConcat` funkcję jako czystą funkcję.  
  
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
  
 Ta wersja generuje ten sam wiersz danych wyjściowych: `StringOne-StringTwo`. Należy pamiętać, że aby zachować łączną wartość, jest ona przechowywana w zmiennej `s2`pośredniej.  
  
 Jednym z metod, które może być bardzo przydatne, jest zapisanie funkcji, które są w sposób nieczysty (to oznacza, że deklarują i modyfikują zmienne lokalne), ale są globalnie czyste. Takie funkcje mają wiele pożądanych cech tworzenia, ale unikają niektórych bardziej zawiłeych idiomy programowania, takich jak korzystanie z rekursji, gdy pętla prosta osiągnie tę samą wartość.  
  
## <a name="standard-query-operators"></a>Standardowe operatory zapytań  
 Ważną cechą standardowych operatorów zapytań jest zaimplementowanie ich jako czystych funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań —C#omówienie ()](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a Programowanie bezwzględne (C#)](./functional-programming-vs-imperative-programming.md)
