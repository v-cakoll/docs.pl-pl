---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a>/optimize
Włącza lub wyłącza optymalizacje kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalny. `/optimize-` Opcja wyłącza optymalizacje kompilatora. `/optimize+` Opcja włącza optymalizacje. Optymalizacje są domyślnie wyłączone.|  
  
## <a name="remarks"></a>Uwagi  
 Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora. Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `/optimize+` może utrudnić debugowania.  
  
 Wszystkie moduły wygenerowane z `/target:module` dla zestawu musi używać tego samego `/optimize` ustawienia jako zestaw. Aby uzyskać więcej informacji, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Możesz połączyć ze sobą `/optimize` i `/debug` opcje.  
  
|Aby ustawić / optimize w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.<br />     Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane** przycisku.<br />4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
