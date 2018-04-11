---
title: '&#39; Wszelkie &#39; nie jest obsługiwany w &#39; Declare &#39; instrukcje'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39; Wszelkie &#39; nie jest obsługiwany w &#39; Declare &#39; instrukcje
`Any` — Typ danych została użyta z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na stosowanie argumentów zawierających dane dowolnego typu. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Przeładowanie, jednak obsługuje i tak powoduje, że `Any` przestarzałe typu danych.  
  
 **Identyfikator błędu:** BC30828  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklarowanie parametrów określonego typu, który ma zostać użyty. na przykład.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` jest oczekiwane przez procedury wywoływanej.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Wskazówki: Wywoływanie Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)
