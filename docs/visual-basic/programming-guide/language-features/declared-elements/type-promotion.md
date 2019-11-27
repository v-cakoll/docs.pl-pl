---
title: Promocja typu
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
ms.openlocfilehash: aa05bd7dc87510aedb0facadf4b7590c8ec57d1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345273"
---
# <a name="type-promotion-visual-basic"></a>Promocja typu (Visual Basic)
Kiedy deklarujesz element programowania w module, Visual Basic promuje swój zakres do przestrzeni nazw zawierającej moduł. Jest to tzw. *Promocja typu*.  
  
 Poniższy przykład przedstawia definicję szkieletu modułu i dwóch członków tego modułu.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 W `projModule`elementy programistyczne zadeklarowane na poziomie modułu są podwyższane do `projNamespace`. W poprzednim przykładzie `basicEnum` i `innerClass` są awansowane, ale `numberSub` nie jest, ponieważ nie jest zadeklarowany na poziomie modułu.  
  
## <a name="effect-of-type-promotion"></a>Efekt promocji typu  
 Efektem promocji typu jest to, że ciąg kwalifikacji nie musi zawierać nazwy modułu. Poniższy przykład wykonuje dwa wywołania procedury w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 W poprzednim przykładzie pierwsze wywołanie używa kompletnych ciągów kwalifikacyjnych. Nie jest to jednak konieczne ze względu na promocję typu. Drugie wywołanie również uzyskuje dostęp do członków modułu bez uwzględniania `projModule` w ciągach kwalifikacji.  
  
## <a name="defeat-of-type-promotion"></a>Sprawowanie promocji typu  
 Jeśli przestrzeń nazw ma już element członkowski o takiej samej nazwie jak element członkowski modułu, podwyższanie poziomu dla tego elementu członkowskiego modułu zostanie poddana przeniesieniu. Poniższy przykład przedstawia definicję szkieletu wyliczenia i modułu w tej samej przestrzeni nazw.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 W poprzednim przykładzie Visual Basic nie można podwyższyć poziomu `abc` klasy do `thisNameSpace`, ponieważ istnieje już Wyliczenie o tej samej nazwie na poziomie przestrzeni nazw. Aby uzyskać dostęp do `abcSub`, należy użyć pełnej `thisNamespace.thisModule.abc.abcSub`ciągu kwalifikacji. Jednak klasy `xyz` nadal są promowane i możesz uzyskać dostęp do `xyzSub` przy użyciu krótszego ciągu kwalifikacji `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Sprawowanie promocji typu dla typów częściowych  
 Jeśli klasa lub struktura wewnątrz modułu używa słowa kluczowego [częściowe](../../../../visual-basic/language-reference/modifiers/partial.md) , promocja typu jest automatycznie obniżana dla tej klasy lub struktury, niezależnie od tego, czy przestrzeń nazw ma element członkowski o tej samej nazwie. Inne elementy w module nadal kwalifikują się do podwyższenia poziomu.  
  
 **Konsekwencj.** Sprawność promocji typu częściowej definicji może spowodować nieoczekiwane wyniki, a nawet błędy kompilatora. Poniższy przykład pokazuje szkieletowe definicje części klasy, z których jedna znajduje się w module.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 W poprzednim przykładzie deweloper może oczekiwać, że kompilator Scala dwie częściowe definicje `sampleClass`. Jednak kompilator nie rozważa podwyższania poziomu definicji częściowej w `sampleModule`. W związku z tym podejmuje próbę skompilowania dwóch oddzielnych i odrębnych klas o nazwie `sampleClass` ale z różnymi ścieżkami kwalifikacyjnymi.  
  
 Kompilator Scala definicje częściowe tylko wtedy, gdy ich w pełni kwalifikowane ścieżki są identyczne.  
  
## <a name="recommendations"></a>Zalecenia  
 Poniższe zalecenia stanowią dobre rozwiązanie programistyczne.  
  
- **Unikatowe nazwy.** Jeśli masz pełną kontrolę nad nazewnictwem elementów programistycznych, zawsze dobrym pomysłem jest używanie unikatowych nazw wszędzie. Identyczne nazwy wymagają dodatkowej kwalifikacji i mogą utrudniać odczytywanie kodu. Mogą również prowadzić do delikatnych błędów i nieoczekiwanych wyników.  
  
- **Pełna kwalifikacje.** Podczas pracy z modułami i innymi elementami w tym samym obszarze nazw najbezpieczniejszym podejściem jest zawsze używanie pełnej kwalifikacji dla wszystkich elementów programistycznych. Jeśli Promocja typu jest obniżana dla elementu członkowskiego modułu i nie masz w pełni kwalifikacji tego elementu członkowskiego, można przypadkowo uzyskać dostęp do innego elementu programistycznego.  
  
## <a name="see-also"></a>Zobacz także

- [Module, instrukcja](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace, instrukcja](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Instrukcje: kontrolowanie zakresu zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
