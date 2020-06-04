---
title: 'Instrukcje: zapisywanie komunikatów dziennika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410052"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Porady: zapisywanie wiadomości rejestru (Visual Basic)

Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o aplikacji. Ten przykład pokazuje, jak używać `My.Application.Log.WriteEntry` metody do rejestrowania informacji o śledzeniu.

Informacje o wyjątku rejestrowania można znaleźć w `My.Application.Log.WriteException` temacie [How to: log Exceptions](how-to-log-exceptions.md).

## <a name="example"></a>Przykład

W tym przykładzie zastosowano `My.Application.Log.WriteEntry` metodę, aby napisać informacje o śledzeniu.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework

Upewnij się, że dane zapisane w dzienniku nie zawierają poufnych informacji, takich jak hasła użytkowników. Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](working-with-application-logs.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
- [Instrukcje: rejestrowanie wyjątków](how-to-log-exceptions.md)
- [Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje](walkthrough-changing-where-my-application-log-writes-information.md)
- [Przewodnik: filtrowanie danych wyjściowych elementu My.Application.Log](walkthrough-filtering-my-application-log-output.md)
