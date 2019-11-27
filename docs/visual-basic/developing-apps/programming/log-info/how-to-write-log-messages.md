---
title: 'Porady: zapisywanie wiadomości rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352056"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Porady: zapisywanie wiadomości rejestru (Visual Basic)

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o aplikacji. W tym przykładzie pokazano, jak za pomocą metody `My.Application.Log.WriteEntry` rejestrować informacje o śledzeniu.

Aby rejestrować informacje o wyjątkach, użyj metody `My.Application.Log.WriteException`. Zobacz [jak: wyjątki dzienników](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

## <a name="example"></a>Przykład

W tym przykładzie zastosowano metodę `My.Application.Log.WriteEntry`, aby napisać informacje o śledzeniu.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Upewnij się, że dane zapisane w dzienniku nie zawierają poufnych informacji, takich jak hasła użytkowników. Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
