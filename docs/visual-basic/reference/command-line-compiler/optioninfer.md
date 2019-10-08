---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: c6fc7e9dcfbce938ad75b0f357c2bfa9cd10703a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005320"
---
# <a name="-optioninfer"></a>-optioninfer
Umożliwia korzystanie z wnioskowania o typie lokalnym w deklaracjach zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalny. Określ `-optioninfer+`, aby włączyć wnioskowanie o typie lokalnym lub `-optioninfer-`, aby go zablokować. Opcja `-optioninfer` bez określonej wartości jest taka sama jak wartość `-optioninfer+`. Wartość domyślna w przypadku nieobecności przełącznika `-optioninfer` jest również `-optioninfer+`. Wartość domyślna jest ustawiana w pliku odpowiedzi VBC. rsp.|  
  
> [!NOTE]
> Możesz użyć opcji `-noconfig`, aby zachować wewnętrzne wartości domyślne kompilatora zamiast opcji określonych w vbc. rsp. Wartość domyślna kompilatora dla tej opcji to `-optioninfer-`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik kodu źródłowego zawiera [instrukcję opcji wnioskowania](../../../visual-basic/language-reference/statements/option-infer-statement.md), instrukcja zastępuje ustawienia kompilatora wiersza polecenia `-optioninfer`.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Aby ustawić-optioninfer w środowisku IDE programu Visual Studio  
  
1. Wybierz projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Na karcie **kompilacja** Zmień wartość w polu **wnioskowanie o opcji** .  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `test.vb` z włączonym wnioskem o typie lokalnym.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
