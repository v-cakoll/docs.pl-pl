---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 220d6e06ef692655bd6db000fa98b4eb2fc69ba9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683849"
---
# <a name="-optionexplicit"></a>-optionexplicit
Powoduje, że kompilator zgłaszaj błędy jeśli zmienne nie są deklarowane, zanim zostaną użyte.  
  
## <a name="syntax"></a>Składnia  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalna. Określ `-optionexplicit+` będą musieli jawnej deklaracji zmiennych. `-optionexplicit+` Opcja jest domyślnie i jest taka sama jak `-optionexplicit`. `-optionexplicit-` Opcja umożliwia niejawne deklaracji zmiennych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik kodu źródłowego zawiera [instrukcji Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), zastępuje instrukcji `-optionexplicit` Ustawienia kompilatora wiersza polecenia.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Aby ustawić - optionexplicit — w środowisku IDE programu Visual Studio  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Zmodyfikuj wartość w **Option Explicit** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje, kiedy `-optionexplicit-` jest używany.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
