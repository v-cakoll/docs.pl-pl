---
title: '&#39;Jako&#39; nie jest obsługiwany w &#39;Declare&#39; — instrukcje'
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
ms.openlocfilehash: d8146e339ac5cb005b99c9a1e02f1cd248c4558b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;Jako&#39; nie jest obsługiwany w &#39;Declare&#39; — instrukcje
`Any` — Typ danych została użyta z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na stosowanie argumentów zawierających dane dowolnego typu. Przeładowanie, jednak obsługuje Visual Basic i tak powoduje, że `Any` przestarzałe typu danych.  
  
 **Identyfikator błędu:** BC30828  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklarowanie parametrów określonego typu, który ma zostać użyty. na przykład.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` jest oczekiwane przez procedury wywoływanej.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)
