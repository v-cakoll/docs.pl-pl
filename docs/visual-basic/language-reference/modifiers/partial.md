---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: 0f74935d58d47e65b5eb614abc86a3fc9c8e6c42
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838368"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Wskazuje częściową definicję typu deklaracji typu.  
  
 Definicję typu między kilka deklaracji można podzielić przy użyciu `Partial` — słowo kluczowe. Można użyć tylu częściowe deklaracje, jak chcesz, tyle plików innego źródła. Jednak wszystkie deklaracje musi należeć do tego samego zestawu i tej samej przestrzeni nazw.  
  
> [!NOTE]
>  Obsługa języka Visual Basic *metod częściowych*, które są zazwyczaj implementowani w klas częściowych. Aby uzyskać więcej informacji, zobacz [metod częściowych](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) i [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attrlist`|Opcjonalna. Lista atrybutów, które są stosowane do tego typu. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ostre (`< >`).|  
|`accessmodifier`|Opcjonalna. Określa, jaki kod może uzyskać dostęp do tego typu. Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalna. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalna. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Wymagana. Nazwa tego typu. Musi być zgodna z nazwą zdefiniowaną w innych częściowe deklaracje tego samego typu.|  
|`Of`|Opcjonalna. Określa, że jest typem ogólnym. Zobacz [typów ogólnych w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md). Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalna. Zobacz [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane w przypadku użycia `Inherits`. Nazwa klasy lub interfejsu, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalna. Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia `Implements`. Nazwy interfejsów, które implementuje tego typu.|  
|`variabledeclarations`|Opcjonalna. Instrukcje, które zadeklarować dodatkowe zmienne i zdarzenia dla tego typu.|  
|`proceduredeclarations`|Opcjonalna. Instrukcje, które deklarowania i definiowania dodatkowych procedur dla typu.|  
|`End Class` lub `End Structure`|Kończy się w tej części `Class` lub `Structure` definicji.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Basic używa definicji częściowej klasy do oddzielania wygenerowanego kodu z utworzonymi przez użytkownika kod w plikach źródłowych oddzielne. Na przykład **projektanta formularzy Windows** definiuje częściowe klasy dla kontrolek, takich jak <xref:System.Windows.Forms.Form>. Kod wygenerowany w tych kontrolek nie należy modyfikować.  
  
 Wszystkie reguły dla klasy, struktury, interfejsu i tworzenia modułu, takich jak użycie modyfikatora i dziedziczenie, zastosowanie przy tworzeniu typu częściowego.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
  
-   W normalnych warunkach należy nie Podziel rozwój jednego typu na dwóch lub więcej deklaracji. W związku z tym, w większości przypadków nie trzeba `Partial` — słowo kluczowe.  
  
-   Aby zwiększyć czytelność, powinien zawierać każdy częściowa deklaracja typu `Partial` — słowo kluczowe. Kompilator umożliwi co najwyżej jeden częściowa deklaracja pominięcie słowa kluczowego. Jeśli co najmniej dwóch Pomiń ją kompilator sygnalizuje błąd.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Unia deklaracji.** Kompilator traktuje typ jako sumę wszystkich częściowe deklaracje. Każdy modyfikator z każdym częściowa definicja odnoszące się do całego typu, a każdy element członkowski z każdym częściowa definicja jest dostępna dla wszystkich typu.  
  
-   **Promocja typu nie jest dozwolona dla typów częściowych w modułach.** Jeśli częściowa definicja znajduje się wewnątrz modułu, promocji typu tego typu jest bezcelowe automatycznie. W takim przypadku zestaw definicje częściowe może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora. Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilator scala definicje częściowe, tylko wtedy, gdy ich w pełni kwalifikowanej ścieżki są identyczne.  
  
 Słowa kluczowego `Partial` można używać w następujących kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dzieli definicję klasy `sampleClass` na dwie deklaracje, z których każdy definiuje innego `Sub` procedury.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Dwie definicje częściowe w poprzednim przykładzie może być w tym samym pliku źródłowym lub w dwóch innych plików źródłowych.  
  
## <a name="see-also"></a>Zobacz także

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
