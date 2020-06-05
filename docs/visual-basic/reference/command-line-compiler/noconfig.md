---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401943"
---
# <a name="-noconfig"></a>-noconfig
Określa, że kompilator nie powinien automatycznie odwoływać się do najczęściej używanych zestawów .NET Framework lub `System` zaimportować `Microsoft.VisualBasic` przestrzenie nazw i.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 `-noconfig`Opcja instruuje kompilator, aby nie kompilować przy użyciu pliku VBC. rsp, który znajduje się w tym samym katalogu, co plik VBC. exe. Plik VBC. rsp odwołuje się do najczęściej używanych zestawów .NET Framework i importuje `System` `Microsoft.VisualBasic` przestrzenie nazw. Kompilator niejawnie odwołuje się do zestawu System. dll, chyba że `-nostdlib` określono opcję. `-nostdlib`Opcja informuje kompilator, że nie kompiluje z VBC. rsp lub automatycznie odwołuje się do zestawu System. dll.  
  
> [!NOTE]
> Zestawy mscorlib. dll i Microsoft. VisualBasic. dll są zawsze wywoływane.  
  
 Plik VBC. rsp można zmodyfikować, aby określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji VBC. exe (z wyjątkiem sytuacji, gdy jest określana `-noconfig` opcja). Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](specify-response-file.md).  
  
 Kompilator przetwarza opcje przesłane do `vbc` ostatniego polecenia. W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku VBC. rsp.  
  
> [!NOTE]
> `-noconfig`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też

- [-nostdlib (Visual Basic)](nostdlib.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [@ (określenie pliku odpowiedzi)](specify-response-file.md)
- [-Reference (Visual Basic)](reference.md)
