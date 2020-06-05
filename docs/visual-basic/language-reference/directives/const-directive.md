---
title: '#Const, dyrektywa'
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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415469"
---
# <a name="const-directive"></a>#Const — dyrektywa

Definiuje warunkowe stałe kompilatora dla Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Części  

 `constname`  
 Wymagany. Nazwa zdefiniowanej stałej.  
  
 `expression`  
 Wymagany. Literał, inna warunkowa stała kompilatora lub dowolna kombinacja, która zawiera wszystkie lub wszystkie operatory arytmetyczne lub logiczne z wyjątkiem `Is` .  
  
## <a name="remarks"></a>Uwagi  

 Warunkowe stałe kompilatora są zawsze prywatne dla pliku, w którym się znajdują. Nie można utworzyć publicznych stałych kompilatora przy użyciu `#Const` dyrektywy; można je utworzyć tylko w interfejsie użytkownika lub za pomocą `/define` opcji kompilatora.  
  
 W programie można używać tylko warunkowych stałych kompilatora i literałów `expression` . Użycie stałej standardowej zdefiniowanej z `Const` powodu błędu. Odwrotnie, można użyć stałych zdefiniowanych ze `#Const` słowem kluczowym tylko dla kompilacji warunkowej. Stałe mogą być również niezdefiniowane, w takim przypadku mają wartość `Nothing` .  
  
## <a name="example"></a>Przykład  

 Ten przykład używa `#Const` dyrektywy.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [-Definiuj (Visual Basic)](../../reference/command-line-compiler/define.md)
- [#If... Then... #Else — dyrektywy](if-then-else-directives.md)
- [Const, instrukcja](../statements/const-statement.md)
- [Kompilacja warunkowa](../../programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else, instrukcja](../statements/if-then-else-statement.md)
