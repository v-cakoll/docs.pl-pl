---
title: Modyfikatory dostępu (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: ec275d4782fee047b16fd114c4d22ceb03eecb11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314112"
---
# <a name="access-modifiers-c-programming-guide"></a>Modyfikatory dostępu (Przewodnik programowania w języku C#)
Wszystkie typy i elementy członkowskie typu ma poziomu ułatwień dostępu, który kontroluje, czy może być używany z innymi kodu z zestawu lub innych zestawów. Następujących modyfikatorów dostępu służy do określenia dostępności typu lub elementu członkowskiego przy deklarowaniu go:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Typ lub element członkowski jest możliwy przez inny kod, w tym samym zestawie lub innego zestawu, który odwołuje się on. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Typ lub element członkowski jest możliwy tylko przez kod w tej samej klasie lub strukturze.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Typ lub element członkowski jest możliwy tylko przez kod w tej samej klasy lub klasa, która jest pochodną klasy.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Typ lub element członkowski jest możliwy przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.  
  
 [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md) typu lub elementu członkowskiego można uzyskać, sprawdzając dowolny kod w zestawie, w którym jest zadeklarowany lub z klasy pochodnej w innym zestawie. 

 [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md) typu lub elementu członkowskiego jest możliwy tylko w deklarowanym zestawie przez kod w tej samej klasy lub typu, który pochodzi od tej klasy.
  
 Poniższe przykłady przedstawiają sposób określić modyfikatorów dostępu dla typu i element członkowski:  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Nie wszystkie modyfikatory dostępu mogą być używane przez wszystkie typy lub elementy członkowskie we wszystkich kontekstach, a w niektórych przypadkach dostępność elementu członkowskiego typu jest ograniczane przez dostępność jej typ zawierający. Poniższe sekcje zawierają szczegółowe informacje o dostępności.  
  
## <a name="class-and-struct-accessibility"></a>Klasy i struktury ułatwień dostępu  
 Klasy i struktury, które są zadeklarowane bezpośrednio z poziomu obszaru nazw (innymi słowy, które nie są zagnieżdżone w innych klasy lub struktury) może być publiczny lub wewnętrzny. Wewnętrzny jest ustawieniem domyślnym, jeśli określono nie modyfikator dostępu.  
  
 Elementy członkowskie struktury, w tym zagnieżdżonych klas i struktur, mogą być deklarowane jako publiczną, wewnętrzny lub prywatny. Klasy elementów członkowskich, w tym zagnieżdżonych klas i struktur, może być publiczny, chroniony, wewnętrzny, chroniony, wewnętrzny, prywatnych, chronionych lub prywatnej. Poziom dostępu do elementów członkowskich klasy i elementy członkowskie struktury, w tym zagnieżdżonych klas i struktur, jest domyślnie prywatne. Prywatne zagnieżdżone typy nie są dostępne z zewnątrz typu zawierającego.  
  
 Klasy pochodne nie mogą mieć większą dostępność niż ich typów podstawowych. Innymi słowy, nie może być klasą publiczną `B` która pochodzi z klasy wewnętrznej `A`. Jeśli były to dozwolone, gdyż miałoby efekt wprowadzania `A` publiczne, ponieważ wszystkie chroniona lub wewnętrzne elementy członkowskie `A` są dostępne w klasie pochodnej.  
  
 Można włączyć określonego innych zestawów dostępu do sieci wewnętrznej typów za pomocą InternalsVisibleToAttribute. Aby uzyskać więcej informacji, zobacz [przyjazne zestawy](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="class-and-struct-member-accessibility"></a>Klasy i dostępność elementu członkowskiego struktury  
 Elementy członkowskie klasy (w tym zagnieżdżonych klas i struktur) mogą być deklarowane z jednym z sześciu typów dostępu. Elementy członkowskie struktury nie można zadeklarować jako chroniony, ponieważ struktur nie obsługują dziedziczenia.  
  
 Zwykle dostępność elementu członkowskiego nie jest większa niż ułatwień dostępu typu, który go zawiera. Jednak publicznego elementu członkowskiego klasy wewnętrzny może być dostępne spoza zestawu, jeśli element członkowski implementuje metody interfejsu lub zastępuje metody wirtualne zdefiniowane w publicznej klasy podstawowej.  
  
 Typ elementu członkowskiego, wszystkie pola, właściwości lub zdarzeń muszą być co najmniej jako dostępne jako członkowski. Podobnie typ zwracany i typy parametrów członka metody, indeksator lub delegata musi być co najmniej jako dostępny jako członkowski. Na przykład nie może mieć publiczną metodę `M` zwracającego klasę `C` chyba że `C` również jest publiczny. Podobnie, nie może mieć właściwość chroniona typu `A` Jeśli `A` jest zadeklarowany jako prywatny.  
  
 Operatory zdefiniowane przez użytkownika musi zawsze być zadeklarowany jako publiczny. Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).  
  
 Finalizatory nie może mieć modyfikatorów dostępności.  
  
 Aby ustawić poziom dostępu dla elementu członkowskiego klasy lub struktury, Dodaj odpowiednie słowo kluczowe do deklaracji elementu członkowskiego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Poziom chronionych wewnętrznych ułatwień dostępu oznacza chroniona lub wewnętrznych nie chronionych i wewnętrzne. Innymi słowy chroniony element członkowski wewnętrznego są dostępne z dowolnej klasy w tym samym zestawie, łącznie z klasy pochodnej. Aby ograniczyć ułatwień dostępu dla tylko klasy pochodnej w tym samym zestawie, deklarowanie wewnętrznych samej klasy i zadeklarować jej elementów członkowskich jako chroniony. Ponadto począwszy od 7.2 C#, umożliwia modyfikator dostępu prywatnego chronionych ten sam efekt bez konieczności przeprowadzania Wewnętrzna klasa zawierająca.  
  
## <a name="other-types"></a>Inne typy  
 Interfejsy zadeklarowany bezpośrednio w przestrzeni nazw mogą być deklarowane jako publiczną ani wewnętrzną i, podobnie jak klasy i struktury, interfejsy domyślnie dostęp do. Elementy członkowskie interfejsu zawsze są publiczne, ponieważ interfejs ma na celu włączyć inne typy dostępu do klasy lub struktury. Brak modyfikatorów dostępu może odnosić się do elementów członkowskich interfejsu.  
  
 Elementy członkowskie wyliczenia zawsze są publiczne, a brak modyfikatorów dostępu mogą być stosowane.  
  
 Obiekty delegowane przypominają klas i struktur. Domyślnie mają one dostęp do po zadeklarowaniu bezpośrednio z poziomu obszaru nazw i dostępu prywatnego podczas zagnieżdżone.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
 [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)
