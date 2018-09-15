---
title: Modyfikatory dostępu (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 6be0ae4f6497dfb2db9607f61c4ede5083d57dc7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617516"
---
# <a name="access-modifiers-c-programming-guide"></a>Modyfikatory dostępu (Przewodnik programowania w języku C#)
Wszystkie typy i elementy członkowskie typu ma poziom ułatwień dostępu, który kontroluje, czy mogą być używane z innym kodem w swoim zestawie lub innych zestawów. Następujące modyfikatory dostępu służy do określania dostępność typu lub elementu członkowskiego, gdy trzeba je zadeklarować:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Typ lub element członkowski może zostać oceniony przez inny kod, w tym samym zestawie lub w innym zestawie, który odwołuje się do niej. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Typu lub element członkowski może zostać oceniony jedynie przez kod w tej samej klasie lub strukturze.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Typu lub element członkowski może zostać oceniony jedynie przez kod z tej samej klasy lub klasy, która jest pochodną klasy.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Typ lub element członkowski może zostać oceniony przez każdy kod z tego samego zestawu, ale nie z innego zestawu.  
  
 [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md) typu lub elementu członkowskiego jest możliwy przez każdy kod w zestawie, w którym jest zdeklarowana lub z poziomu klasy pochodnej w innym zestawie. 

 [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md) typu lub elementu członkowskiego możliwy tylko w deklarowanym zestawie, przez kod w tej samej klasy lub typ, który jest tworzony na podstawie tej klasy.
  
 Poniższe przykłady pokazują, jak określić modyfikatorów dostępu dla typów i elementów członkowskich:  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Nie wszystkie modyfikatory dostępu mogą być używane przez wszystkie typy lub elementy członkowskie we wszystkich kontekstach, a w niektórych przypadkach dostępność składowej typu jest ograniczony przez dostępność jej typ zawierający. Poniższe sekcje zawierają więcej szczegółów na temat ułatwień dostępu.  
  
## <a name="class-and-struct-accessibility"></a>Klasy i struktury w ułatwienia dostępu  
 Klasy i struktury, które są zadeklarowane bezpośrednio w przestrzeni nazw (innymi słowy, które nie są zagnieżdżone w obrębie innych klas lub struktur) może być publiczny lub wewnętrzny. Wewnętrzny jest domyślnym, jeśli nie określono żadnych modyfikator dostępu.  
  
 Składowe struktury, w tym zagnieżdżonych klas i struktur, może być zadeklarowana jako publiczne, wewnętrzne lub prywatnych. Elementy członkowskie, w tym zagnieżdżonych klas i struktur klasy, może być publiczny, chronionych wewnętrznych, chronionych wewnętrznych prywatny chroniony lub prywatnych. Poziom dostępu do składowych klasy i składowe struktury, w tym zagnieżdżonych klas i struktur, jest domyślnie prywatny. Prywatne zagnieżdżone typy nie są dostępne z zewnątrz typu zawierającego.  
  
 Klasy pochodne nie może mieć większą dostępność niż typy podstawowe. Innymi słowy, nie może mieć klasę publiczną `B` pochodząca z klasą wewnętrzną `A`. Jeśli zezwolono na to, gdyż miałoby efekt podejmowanie `A` publiczne, ponieważ wszystkich chronionych i wewnętrznych członków `A` są dostępne w klasie pochodnej.  
  
 Można włączyć określonego innych zestawów, aby uzyskać dostęp do wewnętrznych typów, za pomocą parametru InternalsVisibleToAttribute. Aby uzyskać więcej informacji, zobacz [przyjaznych zestawów](../concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="class-and-struct-member-accessibility"></a>Klasy i dostępność składowej struktury  
 Członkowie klas (w tym zagnieżdżone klasy i struktury) mogą być deklarowane ze wszystkimi sześć typów dostępu. Składowe struktury nie można zadeklarować jako chroniony, ponieważ struktury nie obsługują dziedziczenia.  
  
 Zwykle ułatwień dostępu elementu członkowskiego nie jest większa niż ułatwień dostępu typu, który go zawiera. Jednak publicznej składowej klasy wewnętrznej może być dostępne spoza zestawu, czy element członkowski implementuje metody interfejsu zastępują metody wirtualne, które są zdefiniowane w klasie bazowej.  
  
 Typ dowolnego elementu członkowskiego, który jest pola, właściwości lub zdarzenia musi być co najmniej tak samo dostępna jak ten element członkowski. Podobnie typ zwracany i typy parametrów, dowolnego elementu członkowskiego, który jest metoda, indeksator lub delegata musi być co najmniej tak samo dostępna jak ten element członkowski. Na przykład, nie może mieć publiczną metodę `M` zwracającego klasę `C` chyba że `C` również jest publiczny. Podobnie, nie może mieć właściwość chroniona typu `A` Jeśli `A` jest zadeklarowany jako prywatny.  
  
 Operatory zdefiniowane przez użytkownika musi zawsze być zadeklarowany jako publiczny. Aby uzyskać więcej informacji, zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md).  
  
 Finalizatory nie może mieć modyfikatorów dostępności.  
  
 Aby ustawić poziom dostępu dla elementu członkowskiego klasy lub struktury, Dodaj słowo kluczowe odpowiednie do deklaracji elementu członkowskiego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Poziom chronionych wewnętrznych ułatwień dostępu oznacza, że nie chronionych i wewnętrznych, chronionych i wewnętrznych. Innymi słowy chronionych wewnętrznych elementu członkowskiego jest możliwy z dowolnej klasy w tym samym zestawie, łącznie z klas pochodnych. Aby ograniczyć dostępność do tylko klasy pochodne z tego samego zestawu, Zadeklaruj samej klasy wewnętrznej i zadeklarować składowych jako chroniony. Ponadto począwszy od C# 7.2, możesz użyć modyfikator dostępu prywatnego chronionych aby osiągnąć ten sam wynik nie jest potrzebne zapewnienie klasa zawierająca wewnętrzny.  
  
## <a name="other-types"></a>Inne typy  
 Interfejsy zadeklarowany bezpośrednio w przestrzeni nazw może być zadeklarowany jako publiczny lub wewnętrzny i, podobnie jak klasy i struktury, domyślnie dostęp do interfejsów. Elementy członkowskie interfejsu zawsze są publiczne, ponieważ interfejs ma na celu włączyć inne typy dostępu do klasy lub struktury. Brak modyfikatorów dostępu można zastosować do elementów członkowskich interfejsu.  
  
 Elementy członkowskie wyliczenia zawsze są publiczne, a brak modyfikatorów dostępu mogą być stosowane.  
  
 Delegaty zachowują się jak klas i struktur. Domyślnie mają wewnętrzne dostępu podczas zadeklarowany bezpośrednio w ramach przestrzeni nazw i prywatny dostęp, gdy zagnieżdżony.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
- [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [struct](../../../csharp/language-reference/keywords/struct.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)
