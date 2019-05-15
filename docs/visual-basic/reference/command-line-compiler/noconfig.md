---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: b707899c845b6b08e008fe229497f682c930044a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588846"
---
# <a name="-noconfig"></a>-noconfig
Określa, że kompilator powinien automatycznie odwołuje się do często używanych zestawów .NET Framework lub zaimportować `System` i `Microsoft.VisualBasic` przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 `-noconfig` Opcja informuje kompilator, aby nie kompilacji z soubor Vbc.rsp, który znajduje się w tym samym katalogu co plik Vbc.exe. Soubor Vbc.rsp odwołuje się do często używanych zestawów .NET Framework i importuje `System` i `Microsoft.VisualBasic` przestrzeni nazw. Kompilator niejawnie odwołuje się do zestawu System.dll chyba że `-nostdlib` określono opcję. `-nostdlib` Opcja informuje kompilator, aby nie kompilować z Vbc.rsp lub automatycznie odwołuje się do zestawu System.dll.  
  
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
