---
title: -optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7df1c873c166def9fde1bedc139470263e3e4437
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
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
|`+` &#124; `-`|Opcjonalny. `-optimize-` Opcja wyłącza optymalizacje kompilatora. `-optimize+` Opcja włącza optymalizacje. Optymalizacje są domyślnie wyłączone.|  
  
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
