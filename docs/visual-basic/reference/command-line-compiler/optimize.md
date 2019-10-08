---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005372"
---
# <a name="-optimize"></a>-optimize
Włącza lub wyłącza optymalizacje kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalny. Opcja `-optimize-` wyłącza optymalizacje kompilatora. Opcja `-optimize+` umożliwia optymalizacje. Optymalizacje są domyślnie wyłączone.|  
  
## <a name="remarks"></a>Uwagi  
 Optymalizacje kompilatora sprawiają, że plik wyjściowy jest mniejszy, szybszy i bardziej wydajny. Jednakże, ponieważ optymalizacje powodują zmianę układu kodu w pliku wyjściowym, `-optimize+` może utrudniać debugowanie.  
  
 Wszystkie moduły wygenerowane z `-target:module` dla zestawu muszą używać tych samych ustawień `-optimize` jako zestawu. Aby uzyskać więcej informacji, zobacz [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Można połączyć opcje `-optimize` i `-debug`.  
  
|Aby ustawić-optymalizować w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.<br />     <br />2. Kliknij kartę **kompilacja** .<br />3. kliknij przycisk **Zaawansowane** .<br />4. Zmodyfikuj pole wyboru **Włącz optymalizacje** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
