---
title: 'Instrukcje: zapisywanie komunikatów dziennika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352056"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Porady: zapisywanie wiadomości rejestru (Visual Basic)

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o aplikacji. Ten przykład pokazuje, `My.Application.Log.WriteEntry` jak używać metody do rejestrowania informacji o śledzeniu.

Aby rejestrować informacje o wyjątkach, `My.Application.Log.WriteException` należy użyć metody; Zobacz [jak: wyjątki dzienników](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

## <a name="example"></a>Przykład

W tym przykładzie zastosowano `My.Application.Log.WriteEntry` metodę, aby napisać informacje o śledzeniu.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Upewnij się, że dane zapisane w dzienniku nie zawierają poufnych informacji, takich jak hasła użytkowników. Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: filtrowanie danych wyjściowych elementu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
