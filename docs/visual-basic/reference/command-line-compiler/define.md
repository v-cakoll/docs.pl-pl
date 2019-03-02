---
title: -Definiowanie (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: c21223cc353b7a4614511aa97340c6bc5d61e70e
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200661"
---
# <a name="-define-visual-basic"></a>-Definiowanie (Visual Basic)
Definiuje stałe warunkowe kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`symbol`|Wymagana. Aby zdefiniować symbol.|  
|`value`|Opcjonalna. Wartość do przypisania `symbol`. Jeśli `value` jest ciągiem, muszą być ujęte przez sekwencje ukośnik odwrotny — cudzysłów (\\") zamiast znaki cudzysłowu. Jeśli nie określono wartości, a następnie jest traktowana jako wartość True.|  
  
## <a name="remarks"></a>Uwagi  
 `-define` Opcji obowiązuje, podobnie jak przy użyciu `#Const` dyrektywy preprocesora w pliku źródłowym, z wyjątkiem tego stałe zdefiniowane za pomocą `-define` były publiczne i zastosować do wszystkich plików w projekcie.  
  
 Można użyć symboli utworzone przez tę opcję z `#If`... `Then`... `#Else` dyrektywy, aby warunkowo skompilować pliki źródłowe.  
  
 `-d` jest to forma krótka `-define`.  
  
 Można zdefiniować wiele symboli z `-define` za pomocą przecinków do oddzielenia definicje symbolu.  
  
|Aby ustawić / define w programie Visual Studio zintegrowane środowisko projektowe|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane**.<br />4.  Zmodyfikuj wartość w **stałe niestandardowe** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje, a następnie używa dwóch warunkowe stałe kompilatora.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
