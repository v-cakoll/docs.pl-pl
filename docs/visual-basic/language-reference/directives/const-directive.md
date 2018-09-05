---
title: '##Const — dyrektywa (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 58d786c5e16b1e667f7c7c78b0f7857cd9711239
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541617"
---
# <a name="const-directive"></a>#Const — dyrektywa
Definiuje stałe warunkowe kompilatora dla języka Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>Części  
 `constname`  
 Wymagane. Nazwa — stała definiowanego.  
  
 `expression`  
 Wymagane. Literał, inne stałe warunkowe kompilatora lub dowolną kombinację, który zawiera dowolnych lub wszystkich operatorów arytmetycznych lub logiczne, z wyjątkiem `Is`.  
  
## <a name="remarks"></a>Uwagi  
 Warunkowe stałe kompilatora są zawsze prywatne dla pliku, w jakiej są wyświetlane. Nie można utworzyć stałe kompilatora publicznych, przy użyciu `#Const` dyrektywę; można je utworzyć, tylko w interfejsie użytkownika lub za pomocą `/define` — opcja kompilatora.  
  
 Można użyć tylko warunkowe stałe kompilatora i literały w `expression`. Przy użyciu standardowych stałą zdefiniowane za pomocą `Const` powoduje błąd. Z drugiej strony, można użyć stałe zdefiniowane za pomocą `#Const` — słowo kluczowe tylko w przypadku kompilacji warunkowej. Stałe również może być niezdefiniowana, w którym to przypadku mają wartość `Nothing`.  
  
## <a name="example"></a>Przykład  
 Dyrektywa `#Const` została użyta w poniższym przykładzie.  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
