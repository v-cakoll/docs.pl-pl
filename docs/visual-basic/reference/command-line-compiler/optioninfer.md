---
title: -optioninfer —
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: f1dcc03a67880727893e55c13d65a804586b3f56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788924"
---
# <a name="-optioninfer"></a>-optioninfer —
Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalna. Określ `-optioninfer+` włączyć wnioskowanie o typie lokalnym, lub `-optioninfer-` do jego blokowania. `-optioninfer` Opcji bez wartości określone, jest taka sama jak `-optioninfer+`. Wartość domyślna, gdy `-optioninfer` nie ma przełącznika jest również `-optioninfer+`. Wartość domyślna jest ustawiana w pliku odpowiedzi Vbc.rsp.|  
  
> [!NOTE]
>  Możesz użyć `-noconfig` opcję, aby zachować ustawienia domyślne wewnętrznych kompilatora, zamiast określone w vbc.rsp. Domyślna wartość kompilatora dla tej opcji jest `-optioninfer-`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md), zastępuje instrukcji `-optioninfer` Ustawienia kompilatora wiersza polecenia.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Aby ustawić - optioninfer — w środowisku IDE programu Visual Studio  
  
1. Wybierz projekt w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2. Na **skompilować** Zmień wartość w **Option infer** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `test.vb` z włączoną wnioskowanie o typie lokalnym.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
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
