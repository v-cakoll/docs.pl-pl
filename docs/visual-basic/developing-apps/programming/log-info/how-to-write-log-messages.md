---
title: 'Instrukcje: Zapisywanie wiadomości rejestru (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 007d08917ed5ecae6889d03d820d48e4695c9344
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755327"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Instrukcje: Zapisywanie wiadomości rejestru (Visual Basic)

Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o aplikacji. W tym przykładzie pokazano, jak używać `My.Application.Log.WriteEntry` metody do rejestrowania informacji śledzenia.

Rejestrowanie informacji o wyjątku, użyj `My.Application.Log.WriteException` metoda; zobacz [jak: Rejestrowania wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

## <a name="example"></a>Przykład

W tym przykładzie użyto `My.Application.Log.WriteEntry` metodę, aby zapisać informacje o śledzeniu.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Upewnij się, że dane, które są zapisywane w dzienniku nie zawiera poufne informacje, takie jak hasła użytkownika. Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: Rejestruje wyjątki](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
