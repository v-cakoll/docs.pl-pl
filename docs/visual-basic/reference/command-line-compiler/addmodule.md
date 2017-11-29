---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a>/addmodule
Powoduje, że kompilator wszystkie wpisz informacje z określonym dostępnych plików do projektu są obecnie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagany. Rozdzielana przecinkami lista plików, które zawierają metadanych, ale nie zawierają zestawu manifestów. Nazwy plików zawierających spacje powinny być ujęte w cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 Pliki wyświetlane według `fileList` parametr musi zostać utworzona z `/target:module` opcji lub z innego kompilatora równoważne `/target:module`.  
  
 Wszystkie moduły dodawane z `/addmodule` musi być w tym samym katalogu co plik wyjściowy w czasie wykonywania. Oznacza to, że moduł można określić w dowolnym katalogu, w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania. Jeśli nie jest, możesz uzyskać <xref:System.TypeLoadException> błędu.  
  
 Jeśli określisz (jawnie ani niejawnie) wszelkie[/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opcji innych niż `/target:module` z `/addmodule`, pliki są przekazywane do `/addmodule` staną się częścią zestawu projektu. Zestawu jest wymagana do uruchamiania pliku wyjściowego, który ma jeden lub więcej plików dodane z `/addmodule`.  
  
 Użyj [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Importowanie metadanych z pliku, który zawiera zestaw.  
  
> [!NOTE]
>  `/addmodule` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy moduł.  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 Poniższy kod importuje typów modułów.  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 Po uruchomieniu `t1`, generuje on `802`.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
