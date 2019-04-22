---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819440"
---
# <a name="-noconfig"></a>-noconfig
Określa, czy kompilator powinien automatycznie odwołuje się powszechnie używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawy lub importowania `System` i `Microsoft.VisualBasic` przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 `-noconfig` Opcja informuje kompilator, aby nie kompilacji z soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe. Soubor Vbc.rsp odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw. Kompilator niejawnie odwołuje się do zestawu System.dll chyba że `-nostdlib` określono opcję. `-nostdlib` Opcja informuje kompilator, aby nie kompilować z Vbc.rsp lub automatycznie odwołuje się do zestawu System.dll.  
  
> [!NOTE]
>  Zestawy Mscorlib.dll i Microsoft.VisualBasic.dll zawsze są wywoływane.  
  
 Można zmodyfikować soubor Vbc.rsp, aby określić opcje dodatkowe kompilatora, które powinny być uwzględnione w każdej kompilacji Vbc.exe (z wyjątkiem sytuacji, określając `-noconfig` opcji). Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilator przetwarza opcje przekazywane do `vbc` ostatnie polecenie. W związku z tym dowolnej opcji w wierszu polecenia zastępuje ustawienie tych samych opcji w soubor Vbc.rsp.  
  
> [!NOTE]
>  `-noconfig` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz także

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
