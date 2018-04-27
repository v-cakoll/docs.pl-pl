---
title: Option Infer — Instrukcja
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb6aea2b1e8faf9afd7d252d8828358130fb5374
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="option-infer-statement"></a>Option Infer — Instrukcja
Umożliwia użycie wnioskowania o typie lokalnym przy deklaracji zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`On`|Opcjonalna. Umożliwia wnioskowanie o typie lokalnym.|  
|`Off`|Opcjonalna. Wyłącza wnioskowanie o typie lokalnym.|  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` na początku pliku przed uruchomieniem jakiegokolwiek kodu źródłowego. Jeśli ustawiona wartość `Option Infer` w pliku powoduje konflikt z wartością ustawioną w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.  
  
 Podczas ustawiania `Option Infer` do `On`, zmienne lokalne mogą zadeklarować bez jawne określenie typu danych. Kompilator wnioskuje typ danych zmiennej typu jej wyrażenia inicjowania.  
  
 Na poniższej ilustracji `Option Infer` jest włączona. W deklaracji zmiennej `Dim someVar = 2` jest zadeklarowany jako liczba całkowita przez wnioskowanie o typie.  
  
 ![Widok IntelliSense deklaracji. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
IntelliSense po włączeniu Option Infer  
  
 Na poniższej ilustracji `Option Infer` jest wyłączona. W deklaracji zmiennej `Dim someVar = 2` jest zadeklarowany jako `Object` przez wnioskowanie o typie. W tym przykładzie **Option Strict** mają ustawioną wartość **poza** na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 ![Widok IntelliSense deklaracji. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
IntelliSense po Option Infer jest wyłączone  
  
> [!NOTE]
>  Jeśli zmienna jest zadeklarowana jako `Object`, typu run-time można zmienić, gdy program jest uruchomiony. Visual Basic wykonuje operacje o nazwie *boxing* i *rozpakowującej* konwersję między `Object` a typem wartości, dzięki czemu wykonanie wolniej. Aby uzyskać informacje o konwersji boxing i konwersja unboxing, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 Wnioskowanie o typie stosuje na poziomie procedury i nie ma zastosowania poza procedury w klasy, struktury, modułu lub interfejs.  
  
 Aby uzyskać dodatkowe informacje, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Gdy Option Infer — instrukcja nie jest obecny  
 Jeśli kod źródłowy nie zawiera `Option Infer` instrukcji, **Option Infer** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. Jeśli używana jest kompilatora wiersza polecenia, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) — opcja kompilatora jest używany.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Aby ustawić Option Infer w środowisku IDE  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Ustaw wartość **Option infer** pole.  
  
 Podczas tworzenia nowego projektu **Option Infer** ustawienie **skompilować** ustawiono kartę **Option Infer** ustawienie **domyślne VB** okno dialogowe. Aby uzyskać dostęp do **domyślne VB** okna dialogowego, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej w **domyślne VB** jest `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Aby ustawić Option Infer w wierszu polecenia  
  
-   Obejmują [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="default-data-types-and-values"></a>Dane domyślne typy i wartości  
 W poniższej tabeli przedstawiono wyniki określający typ danych oraz inicjator w różnych kombinacji `Dim` instrukcji.  
  
|Określony typ danych?|Inicjator określona?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączone, występuje błąd kompilacji.|  
|Nie|Tak|`Dim qty = 5`|Jeśli `Option Infer` znajduje się na (ustawienie domyślne), typ zmiennej przyjmuje dane inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączony, zmienna ma typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, występuje błąd kompilacji.|  
|Tak|Nie|`Dim qty As Integer`|Zmienna jest ustawiana na wartość domyślną dla typu danych. Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych Inicjator nie jest możliwe do przekonwertowania na określony typ danych, występuje błąd kompilacji.|  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano sposób `Option Infer` instrukcji umożliwia wnioskowanie o typie lokalnym.  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, że typu run-time może się różnić, gdy zmienna zostanie zidentyfikowana jako `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Okno dialogowe Opcje domyślne, projektów, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Konwersja boxing i konwersja unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
