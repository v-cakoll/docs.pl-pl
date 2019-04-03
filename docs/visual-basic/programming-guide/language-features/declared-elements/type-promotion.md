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
ms.openlocfilehash: f7ac6bfb944da8bd50e035ba97b2b513176dc661
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838875"
---
# <a name="type-promotion-visual-basic"></a>Promocja typu (Visual Basic)
Kiedy Deklarujesz element programowania w module, Visual Basic promuje jego zakres, do obszaru nazw, zawierającej moduł. Jest to nazywane *wpisz podwyższania poziomu*.  
  
 Poniższy kod przedstawia definicję szkielet modułu i dwa elementy członkowskie tego modułu.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 W ramach `projModule`, programowania elementy zadeklarowane na poziomie modułu są promowane do `projNamespace`. W powyższym przykładzie `basicEnum` i `innerClass` są promowane, ale `numberSub` jest, ponieważ nie zadeklarowano na poziomie modułu.  
  
## <a name="effect-of-type-promotion"></a>Efekt promocja typu  
 Promocja typu powoduje, ciąg kwalifikacji nie musi zawierać nazwę modułu. Poniższy przykład wykonuje dwa wywołania do procedury w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 W powyższym przykładzie pierwsze wywołanie używa ciągów pełną kwalifikacji. Jednak nie jest to konieczne ze względu na typ podwyższania poziomu. Drugi wywołują również uzyskuje dostęp do modułu elementy członkowskie bez uwzględniania `projModule` w ciągach kwalifikacji.  
  
## <a name="defeat-of-type-promotion"></a>Zakłócające promocja typu  
 Jeśli przestrzeń nazw ma już element członkowski o takiej samej nazwie jako członek modułu, promocji typu jest bezcelowe dla tego elementu członkowskiego modułu. Poniższy przykład pokazuje szkielet definicji wyliczenia i modułu w ramach tej samej przestrzeni nazw.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 W powyższym przykładzie Visual Basic nie można podwyższyć poziomu klasa `abc` do `thisNameSpace` ponieważ wyliczenie o takiej samej nazwie na poziomie przestrzeni nazw już istnieje. Aby uzyskać dostęp do `abcSub`, należy użyć ciągu pełnej kwalifikacji `thisNamespace.thisModule.abc.abcSub`. Jednak klasy `xyz` nadal jest podwyższany, oraz uzyskiwać dostęp `xyzSub` przy użyciu krótszego ciągu kwalifikacji `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Zakłócające promocja typu dla typów częściowych  
 Jeśli korzysta z klasy lub struktury wewnątrz modułu [częściowe](../../../../visual-basic/language-reference/modifiers/partial.md) — słowo kluczowe, promocji typu jest automatycznie bezcelowe dla tej klasy lub struktury, czy przestrzeń nazw ma składową o tej samej nazwie. Inne elementy w module są nadal uprawnieni do skorzystania z promocji typu.  
  
 **Konsekwencje.** Zakłócające promocji typu częściowa definicja może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora. Poniższy przykład pokazuje szkielet definicje częściowe klasy, z których jedna jest wewnątrz modułu.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 W poprzednim przykładzie, deweloper może oczekiwać kompilator, aby scalić dwie definicje częściowe `sampleClass`. Jednak kompilator nie bierze pod uwagę promocji częściowa definicja wewnątrz `sampleModule`. W rezultacie próby kompilacji dwie odrębne i niezależne klasy, o nazwie `sampleClass` , ale z kwalifikacji różnych ścieżek.  
  
 Kompilator scala definicje częściowe, tylko wtedy, gdy ich w pełni kwalifikowanej ścieżki są identyczne.  
  
## <a name="recommendations"></a>Zalecenia  
 Poniższe zalecenia reprezentują dobrą praktykę programistyczną.  
  
-   **Unikatowe nazwy.** Jeśli masz pełną kontrolę nad nazw elementów programowania, zawsze jest dobry pomysł, aby użyć wszędzie, gdzie unikatowe nazwy. Identyczne nazwy wymagają dodatkowych kwalifikacji i kod może być trudniejsze do odczytu. Również może prowadzić do powstawania błędów i nieoczekiwane wyniki.  
  
-   **Pełnej kwalifikacji.** Podczas pracy z modułów i innych elementów w tej samej przestrzeni nazw najbezpieczniejszy podejściem jest zawsze używać pełnej kwalifikacji dla wszystkich elementów programowania. Promocja typu jest bezcelowe członka modułu, ten element członkowski nie pełnej kwalifikacji można przypadkowo uzyskać dostępu do innego elementu programistycznego.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcja Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace, instrukcja](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Instrukcje: Kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
