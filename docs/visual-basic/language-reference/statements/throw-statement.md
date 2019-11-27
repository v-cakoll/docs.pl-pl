---
title: Throw — Instrukcja
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
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352785"
---
# <a name="throw-statement-visual-basic"></a>Throw — Instrukcja (Visual Basic)

Zgłasza wyjątek w ramach procedury.

## <a name="syntax"></a>Składnia

```vb
Throw [ expression ]
```

## <a name="part"></a>Części

`expression`\
Zawiera informacje o wyjątku, który ma zostać zgłoszony. Opcjonalne, gdy znajdują się w instrukcji `Catch`, w przeciwnym razie jest to wymagane.

## <a name="remarks"></a>Uwagi

Instrukcja `Throw` zgłasza wyjątek, który można obsłużyć za pomocą kodu obsługi wyjątków strukturalnych (`Try`...`Catch`...`Finally`) lub kodu obsługi wyjątków bez struktury (`On Error GoTo`). Można użyć instrukcji `Throw`, aby zalewki błędów w kodzie, ponieważ Visual Basic przenosi stos wywołań do momentu znalezienia odpowiedniego kodu obsługi wyjątków.

Instrukcji `Throw` bez wyrażenia można używać tylko w instrukcji `Catch`, w takim przypadku instrukcja ponownie zgłasza wyjątek, który jest obecnie obsługiwany przez instrukcję `Catch`.

Instrukcja `Throw` resetuje stos wywołań dla wyjątku `expression`. Jeśli nie podano `expression`, stos wywołań zostanie pozostawiony bez zmian. Możesz uzyskać dostęp do stosu wywołań dla wyjątku za pomocą właściwości <xref:System.Exception.StackTrace%2A>.

## <a name="example"></a>Przykład

Poniższy kod używa instrukcji `Throw`, aby zgłosić wyjątek:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Zobacz także

- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
