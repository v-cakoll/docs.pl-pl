---
title: for (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 2c099411499c6ca8396c55955bdc634e48caf621
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2018
---
# <a name="for-c-reference"></a>Aby uzyskać (odwołanie w C#)

Za pomocą `for` pętli, można wykonać instrukcji lub blok instrukcji wielokrotnie aż wynikiem obliczenia określonego wyrażenia jest `false`. Tego rodzaju pętli jest przydatne do Iterowanie przez tablice za i inne aplikacje, w których znasz z wyprzedzeniem jak często mają iteracji pętli.
  
## <a name="example"></a>Przykład

W poniższym przykładzie wartość `i` jest wyświetlony w konsoli i zwiększana o 1 podczas każdej iteracji pętli:
  
[!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]
  
[Dla instrukcji](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) w poprzednim przykładzie wykonuje następujące czynności:
  
1.  Po pierwsze, początkowej wartości zmiennej `i` zostanie nawiązane. Ten krok odbywa się tylko raz, niezależnie od tego, jak często powtórzeń pętli. Inicjowanie ten można traktować jako w toku poza procesem pętli.
  
2.  Próba sprawdzenia warunku (`i <= 5`), wartość `i` jest porównywany z 5.
  
    -   Jeśli `i` nie może być większa niż 5, warunek jest `true`, i są wykonywane następujące akcje.  
  
        1.  `Console.WriteLine` Instrukcji w treści pętli Wyświetla wartość `i`.  
  
        2.  Wartość `i` jest zwiększana o 1.  
  
        3.  Zwraca pętli do początku krok 2, aby ponownie sprawdzić warunku.  
  
    -   Jeśli `i` jest większa niż 5, wyrażenie `false`, i zamknąć pętli.  
  
Należy zauważyć, że jeśli początkowa wartość `i` jest większa niż 5, treści pętli nie Uruchom jeszcze raz.

## <a name="sections-of-a-for-statement"></a>Sekcje dla instrukcji
  
Każdy [dla instrukcji](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) definiuje *inicjatora*, *warunku*, i *iterator* sekcje. Następujące sekcje są zazwyczaj określić liczbę iteracji pętli.  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
Sekcje służą do następujących celów:
  
-   W sekcji inicjatora ustawia warunków początkowych. Instrukcje w tej sekcji uruchomić tylko raz, przed wprowadzeniem pętli. Sekcja może zawierać tylko jeden z poniższych dwóch opcji.  
  
    -   Deklaracji i inicjowania zmiennej lokalnej, jak w pierwszym przykładzie (`int i = 1`). Zmienna jest lokalny dla pętli i nie mogą być dostępne spoza pętli.  
  
    -   Zero lub więcej expressons instrukcji z poniższej listy rozdzielonych przecinkami.  
  
        -   [Przypisanie](../../../csharp/language-reference/operators/assignment-operator.md) — instrukcja  
  
        -   Wywołanie metody  
  
        -   Prefiks lub przyrostka [przyrostu](../../../csharp/language-reference/operators/increment-operator.md) wyrażenia, takich jak `++i` lub `i++`  
  
        -   Prefiks lub przyrostka [dekrementacji](../../../csharp/language-reference/operators/decrement-operator.md) wyrażenia, takich jak `--i` lub `i--`  
  
        -   Tworzenie obiektu przy użyciu [nowych](../../../csharp/language-reference/keywords/new-operator.md)  
  
        -   [await](../../../csharp/language-reference/keywords/await.md) wyrażenia  
  
-   Sekcja warunku zawiera wyrażenie logiczne, które jest obliczane czy pętli powinny być kończone, czy powinno być ono uruchomione ponownie.  
  
-   Sekcja iteratora definiuje, co się stanie po każdej iteracji pętli treści. Sekcja iteratora zawiera zero lub więcej z następujących wyrażenia instrukcji, oddzielonych przecinkami:  
  
    -   [Przypisanie](../../../csharp/language-reference/operators/assignment-operator.md) — instrukcja  
  
    -   Wywołanie metody  
  
    -   Prefiks lub przyrostka [przyrostu](../../../csharp/language-reference/operators/increment-operator.md) wyrażenia, takich jak `++i` lub `i++`  
  
    -   Prefiks lub przyrostka [dekrementacji](../../../csharp/language-reference/operators/decrement-operator.md) wyrażenia, takich jak `--i` lub `i--`  
  
    -   Tworzenie obiektu przy użyciu [nowych](../../../csharp/language-reference/keywords/new-operator.md)  
  
    -   [await](../../../csharp/language-reference/keywords/await.md) wyrażenia  
  
-   Treści pętli zawiera instrukcję, pustą instrukcję lub blok instrukcji, tworzonych przez otaczającej instrukcji zero lub więcej w nawiasach klamrowych.  
  
     Mogą być dzielone z `for` pętli przy użyciu [podziału](../../../csharp/language-reference/keywords/break.md) — słowo kluczowe, lub można krok do następnej iteracji przy użyciu [kontynuować](../../../csharp/language-reference/keywords/continue.md) — słowo kluczowe. Za pomocą może zostać wyjść żadnych pętli [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji.  
  
Pierwszym przykładzie w tym temacie przedstawiono najbardziej typowe rodzaj `for` pętli, co sprawia, że następujące możliwości sekcje:
  
-   Inicjator deklaruje i inicjuje zmiennej lokalnej `i`, który przechowuje liczba powtórzeń pętli.  
  
-   Warunek sprawdza wartości zmiennej pętli względem żadnej znanej wartości końcowej 5.  
  
-   Sekcja iteratora używa instrukcję operatory przyrostka inkrementacji `i++`, aby sprawdzać każdej iteracji pętli.

## <a name="more-examples"></a>Więcej przykładów
  
Poniższy przykład przedstawia kilka mniej typowe opcje: przypisywanie wartości do zmiennej pętli zewnętrznych w sekcji inicjatora, wywoływania `Console.WriteLine` metody zarówno inicjator i sekcje iteratora oraz zmienianie wartości dwu zmienne w sekcji iteratora.
  
[!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
Wszystkie wyrażenia, które definiują `for` instrukcji są opcjonalne. Na przykład następująca instrukcja tworzy Pętla nieskończona:
  
[!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a>specyfikacja języka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Zobacz także

[For — instrukcja (specyfikacja języka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[Odwołanie w C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
[for, instrukcja (C++)](/cpp/cpp/for-statement-cpp)  
[Instrukcje iteracji](../../../csharp/language-reference/keywords/iteration-statements.md)
