---
title: "Typy wskaźników (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe7b926bdf9f662d25f2fe960b51fc8254b7aa3a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="pointer-types-c-programming-guide"></a>Typy wskaźników (Przewodnik programowania w języku C#)
W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym. Deklaracja typu wskaźnika ma jedną z następujących form:  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 Dowolny z następujących typów może być typem wskaźnika:  
  
-   [SByte —](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [ długie](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), [dziesiętną](../../../csharp/language-reference/keywords/decimal.md), lub [bool](../../../csharp/language-reference/keywords/bool.md).  
  
-   Wszelkie [wyliczenia](../../../csharp/language-reference/keywords/enum.md) typu.  
  
-   Dowolny typ wskaźnika.  
  
-   Dowolny typ struktury zdefiniowany przez użytkownika, który zawiera tylko pola niezarządzanych typów.  
  
 Typy wskaźników dziedziczy [obiektu](../../../csharp/language-reference/keywords/object.md) i konwersji między typami wskaźników i `object`. Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania. Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.  
  
 W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika. Na przykład:  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 Wskaźnik nie może wskazywać na odwołania lub do [struktury](../../../csharp/language-reference/keywords/struct.md) zawierający odwołań, ponieważ odwołanie do obiektu może być bezużytecznych nawet wtedy, gdy wskaźnik wskazuje go. Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.  
  
 Wartość zmiennej wskaźnika typu `myType*` adres zmiennej typu `myType`. Poniżej przedstawiono przykłady deklaracji typów wskaźnika:  
  
|Przykład|Opis|  
|-------------|-----------------|  
|`int* p`|`p` jest wskaźnik do wartości całkowitej.|  
|`int** p`|`p` jest wskaźnik na wskaźnik do wartości całkowitej.|  
|`int*[] p`|`p` jest jednowymiarowej tablicy wskaźników do liczb całkowitych.|  
|`char* p`|`p` jest wskaźnik do znaku.|  
|`void* p`|`p` jest wskaźnik do nieznanego typu.|  
  
 Operatora pośredniego wskaźnika * można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową. Na przykład przeanalizujmy następującą deklarację:  
  
```  
int* myVariable;  
```  
  
 Wyrażenie `*myVariable` oznacza `int` znaleziono pod adresem zawarte w zmiennej `myVariable`.  
  
 Istnieje kilka przykładów wskaźniki w tematach [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) i [konwersje wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).  W poniższym przykładzie przedstawiono potrzebę `unsafe` — słowo kluczowe i `fixed` instrukcji i jak zwiększać wskaźnik wewnętrzny.  Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić. (Należy pamiętać o włączeniu niebezpieczny kod w **projektanta projektu**; wybierz **projektu**, **właściwości** menu, a następnie wybierz opcję **niebezpiecznego kodu** w **kompilacji** kartę.)  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 Nie można zastosować operator pośredni wskaźnik typu `void*`. Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.  
  
 Wskaźnik może być `null`. Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.  
  
 Należy pamiętać, że przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie. Należy wziąć pod uwagę metodę, która zwraca wskaźnik do zmiennej lokalnej za pośrednictwem `in`, `out` lub `ref` parametru lub w wyniku funkcji. Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.  
  
 W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:  
  
|Operator/instrukcja|Zastosowanie|  
|-------------------------|---------|  
|*|Wykonuje operację wskaźnika pośredniego.|  
|->|Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.|  
|[]|Indeksuje wskaźnik.|  
|`&`|Uzyskuje adres zmiennej.|  
|++ oraz --|Zwiększa i zmniejsza wartość wskaźnika.|  
|+ oraz -|Wykonuje operacje arytmetyczne na wskaźniku.|  
|==,! =, \<, >, \<=, a > =|Porównuje wskaźniki.|  
|`stackalloc`|Przydziela pamięć na stosie.|  
|`fixed` — Instrukcja|Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.|  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Konwersje wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)  
 [Konwersja boxing i konwersja unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
