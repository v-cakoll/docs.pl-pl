---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005434"
---
# <a name="-noconfig"></a>-noconfig
Określa, że kompilator nie powinien automatycznie odwoływać się do najczęściej używanych zestawów .NET Framework lub zaimportować przestrzenie nazw `System` i `Microsoft.VisualBasic`.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-noconfig` instruuje kompilator, aby nie kompilować przy użyciu pliku VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe. Plik VBC. rsp odwołuje się do najczęściej używanych zestawów .NET Framework i importuje przestrzenie nazw `System` i `Microsoft.VisualBasic`. Kompilator niejawnie odwołuje się do zestawu System. dll, chyba że jest określona opcja `-nostdlib`. Opcja `-nostdlib` instruuje kompilator, aby nie kompilować z VBC. rsp lub automatycznie odwoływać się do zestawu System. dll.  
  
> [!NOTE]
> Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.  
  
 Plik VBC. rsp można zmodyfikować, aby określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji VBC. exe (z wyjątkiem sytuacji, gdy określono opcję `-noconfig`). Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 Kompilator przetwarza opcje przesłane do `vbc` polecenie Last. W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku VBC. rsp.  
  
> [!NOTE]
> Opcja `-noconfig` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz także

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
