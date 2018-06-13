---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649948"
---
# <a name="-optimize"></a>-optimize
Włącza lub wyłącza optymalizacje kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalna. `-optimize-` Opcja wyłącza optymalizacje kompilatora. `-optimize+` Opcja włącza optymalizacje. Optymalizacje są domyślnie wyłączone.|  
  
## <a name="remarks"></a>Uwagi  
 Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora. Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `-optimize+` może utrudnić debugowania.  
  
 Wszystkie moduły wygenerowane z `-target:module` dla zestawu musi używać tego samego `-optimize` ustawienia jako zestaw. Aby uzyskać więcej informacji, zobacz [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Możesz połączyć ze sobą `-optimize` i `-debug` opcje.  
  
|Aby ustawić - optymalizowania w Visual Studio zintegrowane środowisko programistyczne|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.<br />     <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane** przycisku.<br />4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
