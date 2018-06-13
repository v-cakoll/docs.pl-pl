---
title: Kontrola dostępu (F#)
description: 'Informacje o sposobie kontrolowania dostępu do elementów programowania, takich jak typy, metod i funkcje w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 0a5cc1faa1aef343aaca0abb0c42a0dd9a52fcbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566525"
---
# <a name="access-control"></a>Kontrola dostępu

*Kontrola dostępu* odwołuje się do deklarowania, których klienci mogą używać niektórych elementów programów, takich jak typy, metod i funkcje.


## <a name="basics-of-access-control"></a>Podstawowe informacje dotyczące kontroli dostępu
W języku F #, kontroli dostępu w specyfikatory `public`, `internal`, i `private` można zastosować do modułów, typy metod, definicje wartości, funkcji, właściwości i pola jawne.


- `public` Wskazuje, czy jednostka jest dostępna przez wszystkie obiekty wywołujące.

- `internal` Wskazuje, że jednostka jest możliwy tylko z tego samego zestawu.

- `private` Wskazuje, że jednostka jest możliwy tylko z otaczającym typu lub modułu.


>[!NOTE] 
Specyfikator dostępu `protected` nie jest używana w języku F #, chociaż jest dopuszczalne, jeśli używasz typy utworzone w językach, które obsługują `protected` dostępu. W związku z tym w przypadku przesłonięcia Metoda chroniona metodę pozostaje dostępna tylko w klasie i jego elementów podrzędnych.

Ogólnie rzecz biorąc, specyfikator jest umieszczany przed nazwą podmiotu, chyba że `mutable` lub `inline` specyfikator jest używana, które występują po specyfikatora dostępu.

Jeśli nie specyfikatora dostępu jest używana, wartością domyślną jest `public`, z wyjątkiem `let` powiązania w typie, które są zawsze `private` do typu.

Podpisy w języku F # Podaj inny mechanizm kontroli dostępu do elementów programu F #. Podpisy nie są wymagane do kontroli dostępu. Aby uzyskać więcej informacji, zobacz [podpisy](signatures.md).


## <a name="rules-for-access-control"></a>Zasady kontroli dostępu
Kontrola dostępu podlega następujące reguły:


- Deklaracje dziedziczenia (oznacza to, że korzystanie z `inherit` określić klasę podstawową dla klasy) interfejsu deklaracje (które określając, że klasa implementuje interfejs) i abstrakcyjne elementy członkowskie zawsze mieć tą samą dostępnością, typ otaczający. W związku z tym specyfikatora dostępu nie można używać w tych konstrukcji.

- Poszczególnych przypadków Unii rozłącznych nie może mieć własne niezależnie od typu union Modyfikatory kontroli dostępu.

- Poszczególne pola typu rekordu nie może mieć własne niezależnie od typu rekordu Modyfikatory kontroli dostępu.


## <a name="example"></a>Przykład
Poniższy kod przedstawia użycie specyfikatorów kontroli dostępu. Istnieją dwa pliki w projekcie `Module1.fs` i `Module2.fs`. Każdy plik jest niejawnie modułu. Dlatego istnieją dwa moduły `Module1` i `Module2`. Prywatny typ i wewnętrzny typ są zdefiniowane w `Module1`. Prywatny typ nie ma dostępu z `Module2`, ale wewnętrzny typ można.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
Poniższy kod sprawdza dostępność typy utworzone w `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Podpisy](signatures.md)
