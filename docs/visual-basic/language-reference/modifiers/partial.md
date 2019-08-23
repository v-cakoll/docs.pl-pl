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
ms.openlocfilehash: dd7550b8b1e164c55bd97828d395b43a60c87cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929950"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
Wskazuje, że deklaracja typu jest częściową definicją typu.  
  
 Można podzielić definicję typu między kilka deklaracji za pomocą `Partial` słowa kluczowego. Możesz użyć dowolną liczbę deklaracji częściowych, tak jak wiele różnych plików źródłowych. Wszystkie deklaracje muszą jednak znajdować się w tym samym zestawie i w tej samej przestrzeni nazw.  
  
> [!NOTE]
> Visual Basic obsługuje *metody częściowe*, które zwykle są implementowane w klasach częściowych. Aby uzyskać więcej informacji, zobacz [częściowe metody](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) i [Sub instrukcji](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
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
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego typu. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy kątowe (`< >`).|  
|`accessmodifier`|Opcjonalna. Określa kod, który może uzyskać dostęp do tego typu. Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalna. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalna. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Wymagany. Nazwa tego typu. Musi odpowiadać nazwie zdefiniowanej we wszystkich innych deklaracjach częściowych tego samego typu.|  
|`Of`|Opcjonalny. Określa, że jest to typ ogólny. Zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Wymagane w przypadku użycia [programu](../../../visual-basic/language-reference/statements/of-clause.md). Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalna. Zobacz [instrukcje Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane, `Inherits`Jeśli używasz. Nazwa klasy lub interfejsu, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalny. Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane, `Implements`Jeśli używasz. Nazwy interfejsów implementowanych przez ten typ.|  
|`variabledeclarations`|Opcjonalna. Instrukcje, które deklarują dodatkowe zmienne i zdarzenia dla typu.|  
|`proceduredeclarations`|Opcjonalny. Instrukcje, które deklarują i definiują dodatkowe procedury dla typu.|  
|`End Class` lub `End Structure`|Zakończenie tej `Class` częściowej `Structure` lub definicji.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Basic używa definicji klasy częściowej do oddzielenia wygenerowanego kodu od kodu napisanego przez użytkownika w oddzielnych plikach źródłowych. Na przykład **Projektant formularzy systemu Windows** definiuje klasy częściowe dla formantów, takich jak <xref:System.Windows.Forms.Form>. Nie należy modyfikować wygenerowanego kodu w tych kontrolkach.  
  
 W przypadku tworzenia typu częściowego stosowane są wszystkie reguły tworzenia klas, struktur, interfejsów i modułów, takie jak te dla modyfikatorów użycia i dziedziczenia.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
  
- W normalnych warunkach nie należy dzielić na rozwój jednego typu między dwie lub więcej deklaracji. W związku z tym w większości przypadków `Partial` słowo kluczowe nie jest potrzebne.  
  
- W celu zapewnienia czytelności każda częściowa deklaracja typu powinna zawierać `Partial` słowo kluczowe. Kompilator zezwala przynajmniej jednej deklaracji częściowej na pominięcie słowa kluczowego; Jeśli dwa lub więcej pomijają, kompilator sygnalizuje błąd.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Związek deklaracji.** Kompilator traktuje typ jako związek wszystkich jego częściowych deklaracji. Każdy modyfikator od każdej częściowej definicji ma zastosowanie do całego typu, a każdy element członkowski z każdej częściowej definicji jest dostępny dla całego typu.  
  
- **Promocja typu nie jest dozwolona dla typów częściowych w modułach.** Jeśli częściowa definicja znajduje się w module, podwyższanie poziomu tego typu jest automatycznie obniżane. W takim przypadku zestaw częściowych definicji może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora. Aby uzyskać więcej informacji, zobacz [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Kompilator Scala definicje częściowe tylko wtedy, gdy ich w pełni kwalifikowane ścieżki są identyczne.  
  
 Słowa kluczowego `Partial` można używać w następujących kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dzieli definicję klasy `sampleClass` na dwie deklaracje, z których każda definiuje inną `Sub` procedurę.  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Dwie częściowe definicje w poprzednim przykładzie mogą znajdować się w tym samym pliku źródłowym lub w dwóch różnych plikach źródłowych.  
  
## <a name="see-also"></a>Zobacz także

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
