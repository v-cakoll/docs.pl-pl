---
title: Partial (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5129ef7737b1b07317d47f8d18e9aceb668bf05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Wskazuje, że Deklaracja typu jest częściową definicją typu.  
  
 Definicja typu między kilka deklaracji można podzielić przy użyciu `Partial` — słowo kluczowe. Możesz użyć tyle częściowe deklaracje można dowolnie, dowolną liczbę plików innego źródła można dowolnie. Jednak wszystkie deklaracje muszą być w tym samym zestawie i tego samego obszaru nazw.  
  
> [!NOTE]
>  Obsługa języka Visual Basic *metody częściowe*, które są zazwyczaj stosowane w klas częściowych. Aby uzyskać więcej informacji, zobacz [metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) i [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
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
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego typu. Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy (`< >`).|  
|`accessmodifier`|Opcjonalny. Określa, jaki kod mogą uzyskiwać dostęp do tego typu. Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalny. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalny. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Wymagany. Nazwa tego typu. Musi być zgodna z nazwą zdefiniowaną w innych częściowe deklaracje tego samego typu.|  
|`Of`|Opcjonalny. Określa, że jest typem ogólnym. Zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md). Zobacz [typu listy](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalny. Zobacz [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane w przypadku użycia `Inherits`. Nazwa klasy lub interfejsu, w którym ta klasa dziedziczy.|  
|`Implements`|Opcjonalny. Zobacz [implementuje instrukcji](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia `Implements`. Nazwy interfejsów, które implementuje tego typu.|  
|`variabledeclarations`|Opcjonalny. Instrukcje, które deklaruje dodatkowe zmienne i zdarzenia dla typu.|  
|`proceduredeclarations`|Opcjonalny. Instrukcje, które deklaruje i zdefiniować dodatkowe procedury dla typu.|  
|`End Class`lub`End Structure`|Kończy się tym częściowego `Class` lub `Structure` definicji.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Basic używa definicje klas częściowego do oddzielania wygenerowanego kodu z utworzonymi przez użytkownika kodu w plikach źródłowych oddzielne. Na przykład **projektanta formularzy systemu Windows** definiuje częściowej klasy formantów, takich jak <xref:System.Windows.Forms.Form>. Wygenerowany kod w tych kontrolek nie należy modyfikować.  
  
 Wszystkie reguły dla klasy, struktury, interfejsu i Tworzenie modułu, takich jak te dotyczące użycia modyfikator i dziedziczenie, zastosować podczas tworzenia typu częściowego.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
  
-   W normalnych okolicznościach nie należy rozdzielić opracowania jednego typu w deklaracjach dwóch lub więcej. W związku z tym w większości przypadków nie trzeba `Partial` — słowo kluczowe.  
  
-   Aby zwiększyć czytelność, co z częściowa deklaracja typu powinna zawierać `Partial` — słowo kluczowe. Kompilator umożliwia co najwyżej jeden częściowa deklaracja na pominięcie słowa kluczowego. co najmniej dwa pominięcia go kompilator sygnalizuje wystąpił błąd.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Unia deklaracji.** Kompilator traktuje typ jako Unii wszystkie częściowe deklaracje. Każdy modyfikator z każdej definicji częściowej ma zastosowanie do wszystkich typu, a każdy element członkowski z każdej definicji częściowej jest dostępny dla wszystkich typu.  
  
-   **Promocja typu nie jest dozwolona dla typów częściowych w modułach.** Jeśli jest częściową definicją wewnątrz modułu, promocja typu tego typu jest automatycznie bezcelowe. W takim przypadku zestawu definicji częściowej może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora. Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilator scala definicji częściowej tylko wtedy, gdy ich w pełni kwalifikowanej ścieżki są identyczne.  
  
 `Partial` — Słowo kluczowe może być używana w tych sytuacjach:  
  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dzieli definicji klasy `sampleClass` do dwóch deklaracji, z których każdy definiuje innej `Sub` procedury.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 Dwie definicje częściowe w poprzednim przykładzie można w tym samym pliku źródłowego lub w dwóch plikach innego źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
