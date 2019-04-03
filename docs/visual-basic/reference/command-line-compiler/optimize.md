---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842164"
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
|`+` &#124; `-`|Opcjonalna. `-optimize-` Opcja wyłącza optymalizacje kompilatora. `-optimize+` Opcja włącza optymalizacje. Domyślnie są wyłączone optymalizacje.|  
  
## <a name="remarks"></a>Uwagi  
 Plik wyjściowy był optymalizacje kompilatora, mniejszy, szybszy i bardziej wydajne. Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `-optimize+` może utrudnić debugowanie.  
  
 Wszystkie moduły, wygenerowane za pomocą `-target:module` dla zestawu musi używać tego samego `-optimize` ustawienia zgodnie z zestawu. Aby uzyskać więcej informacji, zobacz [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Można połączyć `-optimize` i `-debug` opcje.  
  
|Aby ustawić - optymalizacji w programie Visual Studio zintegrowanego środowiska programistycznego|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.<br />     <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane** przycisku.<br />4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i umożliwia optymalizacje kompilatora.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
