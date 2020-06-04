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
ms.openlocfilehash: 95572b1739490e90f53da6b6ec283bfb532c46d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404138"
---
# <a name="throw-statement-visual-basic"></a>Throw — Instrukcja (Visual Basic)

Zgłasza wyjątek w ramach procedury.

## <a name="syntax"></a>Składnia

```vb
Throw [ expression ]
```

## <a name="part"></a>Część

`expression`\
Zawiera informacje o wyjątku, który ma zostać zgłoszony. Opcjonalne, gdy znajdują się w `Catch` instrukcji, w przeciwnym razie jest to wymagane.

## <a name="remarks"></a>Uwagi

`Throw`Instrukcja zgłasza wyjątek, który można obsłużyć z kodem obsługującym wyjątek strukturalny ( `Try` ... `Catch` ...`Finally`) lub niestrukturalny kod obsługi wyjątków ( `On Error GoTo` ). Możesz użyć instrukcji, `Throw` Aby zalewki błędów w kodzie, ponieważ Visual Basic przesuwa stos wywołań do momentu znalezienia odpowiedniego kodu obsługi wyjątków.

`Throw`Instrukcja bez wyrażenia może być używana tylko w `Catch` instrukcji, w tym przypadku instrukcja ponownie generuje wyjątek, który jest obecnie obsługiwany przez `Catch` instrukcję.

`Throw`Instrukcja resetuje stos wywołań dla `expression` wyjątku. Jeśli `expression` nie jest podany, stos wywołań pozostaje niezmieniony. Możesz uzyskać dostęp do stosu wywołań dla wyjątku za pomocą <xref:System.Exception.StackTrace%2A> właściwości.

## <a name="example"></a>Przykład

Poniższy kod używa instrukcji, `Throw` Aby zgłosić wyjątek:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>Zobacz też

- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
- [On Error, instrukcja](on-error-statement.md)
