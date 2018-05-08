---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig"></a>-noconfig
Określa, że kompilator powinien automatycznie odwołuje się często używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawy lub importu `System` i `Microsoft.VisualBasic` przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 `-noconfig` Opcja informuje kompilator, aby nie kompilacji z pliku Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe. Pliku Vbc.rsp odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów i Importy `System` i `Microsoft.VisualBasic` przestrzeni nazw. Kompilator niejawnie odwołuje się do zestawu System.dll chyba że `-nostdlib` określono opcję. `-nostdlib` Opcja nakazuje kompilatorowi nie kompilacji z Vbc.rsp lub automatycznie odwołuje się do zestawu System.dll.  
  
> [!NOTE]
>  Zawsze odwołuje się do pliku Mscorlib.dll i pliku Microsoft.VisualBasic.dll zestawów.  
  
 Można zmodyfikować pliku Vbc.rsp umożliwia określenie opcji kompilatora dodatkowe, które powinny być uwzględnione w każdej kompilacji Vbc.exe (z wyjątkiem podczas określania `-noconfig` opcja). Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilator przetwarza opcje przekazane do `vbc` ostatniego polecenia. W związku z tym każda opcja, w wierszu polecenia zastępuje ustawienie opcji tego samego pliku Vbc.rsp.  
  
> [!NOTE]
>  `-noconfig` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [-odwołania (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
