---
title: '#<a name="const-directive"></a>Const-dyrektywa'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a>#Const — dyrektywa
Definiuje warunkowe stałe kompilatora Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Części  
 `constname`  
 Wymagany. Nazwa stała jest zdefiniowany.  
  
 `expression`  
 Wymagany. Literał, inne warunkowego kompilatora stałej lub dowolnej kombinacji, która obejmuje dowolnych lub wszystkich operatorów arytmetycznych i logicznych z wyjątkiem `Is`.  
  
## <a name="remarks"></a>Uwagi  
 Warunkowe stałe kompilatora są zawsze prywatne dla pliku, w jakiej widnieją. Nie można utworzyć stałe kompilatora publiczny przy użyciu `#Const` dyrektywy; tylko w interfejsie użytkownika lub można je utworzyć `/define` — opcja kompilatora.  
  
 Można użyć tylko warunkowe stałe kompilatora i literały w `expression`. Przy użyciu standardowych stałą zdefiniowane z `Const` powoduje błąd. Z drugiej strony, można użyć stałe zdefiniowane z `#Const` — słowo kluczowe tylko dla kompilacji warunkowej. Stałe również może być niezdefiniowana, w takim przypadku mają wartość `Nothing`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `#Const` dyrektywy.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const — instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [IF... Następnie... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
