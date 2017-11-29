---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a>/define (Visual Basic)
Definiuje warunkowe stałe kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`symbol`|Wymagany. Symbol do definiowania.|  
|`value`|Opcjonalny. Wartość do przypisania `symbol`. Jeśli `value` jest ciągiem, muszą być ujęte przez sekwencje ukośnik odwrotny cudzysłowu (\\") zamiast znaków cudzysłowu. Jeśli nie określono wartości, a następnie jest traktowana jako True.|  
  
## <a name="remarks"></a>Uwagi  
 `/define` Opcji jest efekt jest podobny do sposobu używania `#Const` dyrektywy preprocesora w pliku źródłowym, z wyjątkiem tego stałe zdefiniowane z `/define` są publiczne i dotyczą wszystkich plików w projekcie.  
  
 Można użyć symboli utworzone przez tę opcję z `#If`... `Then`... `#Else` dyrektywy warunkowo skompilować plików źródłowych.  
  
 `/d`jest krótka forma `/define`.  
  
 Można zdefiniować wiele symboli z `/define` za pomocą przecinka do oddzielania definicji symbolu.  
  
|Aby ustawić / define w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane**.<br />4.  Zmodyfikuj wartość w **stałe niestandardowe** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod definiuje, a następnie używa dwóch warunkowe stałe kompilatora.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
