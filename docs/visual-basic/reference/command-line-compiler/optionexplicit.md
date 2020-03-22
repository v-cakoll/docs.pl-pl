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
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266732"
---
# <a name="-optionexplicit"></a>-optionexplicit
Powoduje, że kompilator do raportowania błędów, jeśli zmienne nie są zadeklarowane przed ich użyciem.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+`&#124;`-`  
 Element opcjonalny. Określ, aby wymagać `-optionexplicit+` jawnej deklaracji zmiennych. Opcja `-optionexplicit+` jest domyślna i jest `-optionexplicit`taka sama jak . Opcja `-optionexplicit-` umożliwia niejawną deklarację zmiennych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik kodu źródłowego zawiera [instrukcję Option](../../../visual-basic/language-reference/statements/option-explicit-statement.md)Explicit `-optionexplicit` , instrukcja zastępuje ustawienie kompilatora wiersza polecenia.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Aby ustawić -optionexplicit w programie Visual Studio IDE  
  
1. Wybierz projekt w **Eksploratorze rozwiązań**. W menu **Projekt** kliknij polecenie **Właściwości**.
  
2. Kliknij kartę **Kompilowanie.**  
  
3. Zmodyfikuj wartość w polu **Opcja Jawna.**  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje, gdy `-optionexplicit-` jest używany.  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Visual Basic Kompilator wiersza polecenia](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
