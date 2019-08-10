---
title: Throw — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 9680700267f17c8e316de351fead61f1dc4aded0
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869020"
---
# <a name="throw-statement-visual-basic"></a>Throw — Instrukcja (Visual Basic)

Zgłasza wyjątek w ramach procedury.

## <a name="syntax"></a>Składnia

```vb
Throw [ expression ]
```

## <a name="part"></a>Części

`expression`\
Zawiera informacje o wyjątku, który ma zostać zgłoszony. Opcjonalne, gdy znajdują się `Catch` w instrukcji, w przeciwnym razie jest to wymagane.

## <a name="remarks"></a>Uwagi

Instrukcja zgłasza wyjątek, który można obsłużyć z kodem obsługującym wyjątek strukturalny`Try`(... `Throw` `Catch`... ) lub kod obsługi wyjątków bez struktury (`On Error GoTo`). `Finally` Możesz użyć `Throw` instrukcji, aby zalewki błędów w kodzie, ponieważ Visual Basic przesuwa stos wywołań do momentu znalezienia odpowiedniego kodu obsługi wyjątków.

Instrukcja bez wyrażenia może być używana tylko `Catch` w instrukcji, w tym przypadku instrukcja ponownie generuje wyjątek, który jest `Catch` obecnie obsługiwany przez instrukcję. `Throw`

Instrukcja resetuje stos wywołań `expression` dla wyjątku. `Throw` Jeśli `expression` nie jest podany, stos wywołań pozostaje niezmieniony. Możesz uzyskać dostęp do stosu wywołań dla wyjątku za pomocą <xref:System.Exception.StackTrace%2A> właściwości.

## <a name="example"></a>Przykład

Poniższy kod używa instrukcji, `Throw` aby zgłosić wyjątek:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Zobacz także

- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
