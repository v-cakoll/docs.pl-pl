---
title: Element „As Any” nie jest obsługiwany w instrukcjach „Declare”
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: c6c792e02bb655dc8a9544c4b5b46a64210556f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839928"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>Element „As Any” nie jest obsługiwany w instrukcjach „Declare”
`Any` — Typ danych był używany z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na korzystanie z argumentów, które mogą zawierać dowolny typ danych. Obsługa języka Visual Basic przeciążenia, jednak i sprawia, że tak `Any` przestarzały typ danych.  
  
 **Identyfikator błędu:** BC30828  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Można deklarować parametrów określonego typu, którego chcesz użyć. na przykład.  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2.  Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` oczekuje przez tę procedurę, wywoływana.  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)
