---
title: -noconfig —
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: bce2d98a8915e80cdecd7b67029b0c872cf70140
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959582"
---
# <a name="-noconfig"></a>-noconfig —
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
  
## <a name="see-also"></a>Zobacz też  
 [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
