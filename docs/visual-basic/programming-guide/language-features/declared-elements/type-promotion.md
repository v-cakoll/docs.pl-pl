---
title: Promocja typu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 104fa906fecc5a5bb8704fe3ab839f9f200cf73b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-promotion-visual-basic"></a>Promocja typu (Visual Basic)
Deklaracja elementu programistycznego w module języka Visual Basic zamienia jego zakresu przestrzeni nazw zawierającej modułu. Jest to nazywane *wpisz podwyższania poziomu*.  
  
 W poniższym przykładzie przedstawiono definicję szkielet modułu i dwa elementy członkowskie tego modułu.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 W ramach `projModule`, programowania elementy zadeklarowane na poziomie modułu awansowane na `projNamespace`. W powyższym przykładzie `basicEnum` i `innerClass` awansowane, ale `numberSub` jest, ponieważ nie jest zadeklarowany na poziomie modułu.  
  
## <a name="effect-of-type-promotion"></a>Efekt promocja typu  
 Promocja typu powoduje ciąg kwalifikacji nie musi zawierać nazwę modułu. Poniższy przykład powoduje, że dwa wywołania do procedury w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 W powyższym przykładzie pierwsze wywołanie używa ciągów pełnej kwalifikacji. Jednak nie jest to konieczne ze względu na typ podwyższania poziomu. Drugi wywołać również uzyskuje dostęp do elementów członkowskich modułu bez uwzględniania `projModule` w ciągach kwalifikacji.  
  
## <a name="defeat-of-type-promotion"></a>Sprawność promocja typu  
 Jeśli przestrzeń nazw ma już element członkowski o takiej samej nazwie jako członek modułu, typu promocji jest bezcelowe dla tego elementu członkowskiego modułu. Poniższy przykład przedstawia definicję szkielet wyliczenie i modułu w ramach tego samego obszaru nazw.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 W powyższym przykładzie Visual Basic nie można podwyższyć poziomu klasy `abc` do `thisNameSpace` , ponieważ istnieje już wyliczenie o tej samej nazwie na poziomie przestrzeni nazw. Aby uzyskać dostęp do `abcSub`, należy użyć ciągu pełnej kwalifikacji `thisNamespace.thisModule.abc.abcSub`. Jednak klasy `xyz` nadal jest podwyższany, uzyskasz dostęp do `xyzSub` z krótszego ciągu kwalifikacji `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Sprawność promocja typu dla typów częściowych  
 Jeśli korzysta z klasy lub struktury wewnątrz modułu [częściowe](../../../../visual-basic/language-reference/modifiers/partial.md) — słowo kluczowe, promocja typu jest automatycznie bezcelowe dla tej klasy lub struktury, czy przestrzeń nazw ma element członkowski o takiej samej nazwie. Inne elementy w module nadal kwalifikują się do typu podwyższania poziomu.  
  
 **Skutki.** Sprawność promocja typu z częściowa definicja może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora. W poniższym przykładzie przedstawiono szkielet definicji częściowej klasy, z których jeden jest wewnątrz modułu.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 W poprzednim przykładzie, deweloper może spodziewać się kompilatora można scalić dwóch definicji częściowej `sampleClass`. Jednak kompilator nie należy wziąć pod uwagę podwyższania poziomu dla definicji częściowej wewnątrz `sampleModule`. W związku z tym próbuje skompilować dwóch oddzielnych klas, o nazwie `sampleClass` , ale z inną kwalifikacji ścieżki.  
  
 Kompilator scala definicji częściowej tylko wtedy, gdy ich w pełni kwalifikowanej ścieżki są identyczne.  
  
## <a name="recommendations"></a>Zalecenia  
 Poniższe zalecenia reprezentują dobrym rozwiązaniem programowania.  
  
-   **Unikatowe nazwy.** Jeśli masz pełną kontrolę nad nazw elementów programowania zawsze jest warto użyć wszędzie unikatowe nazwy. Identycznych nazw wymagają dodatkowe wymagania i wprowadzić kod trudniejsze do odczytu. Również może prowadzić do powstawania błędów i nieoczekiwane wyniki.  
  
-   **Pełnej kwalifikacji.** Podczas pracy z modułów i inne elementy w tej samej przestrzeni nazw najbezpieczniejszym rozwiązaniem jest zawsze użycie pełnej kwalifikacji dla wszystkich elementów programowania. Promocja typu jest bezcelowe dla elementu członkowskiego moduł, możesz nie pełni kwalifikuje się ten element członkowski może przypadkowo uzyskać dostępu do innego elementu programowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Module, instrukcja](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Namespace, instrukcja](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Instrukcje: kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
