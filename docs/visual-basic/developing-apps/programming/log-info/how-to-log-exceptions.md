---
title: 'Instrukcje: rejestrowanie wyjątków'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352084"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Porady: wyjątki rejestru w Visual Basic

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o wyjątkach występujących w aplikacji. W poniższych przykładach pokazano, `My.Application.Log.WriteException` jak używać metody do rejestrowania wyjątków, które są przechwytywane jawnie, oraz wyjątków, które nie są obsługiwane.  
  
 Aby uzyskać informacje o śledzeniu rejestrowania `My.Application.Log.WriteEntry` , użyj metody. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>Aby zarejestrować obsłużony wyjątek  
  
1. Utwórz metodę, która będzie generować informacje o wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Użyj `Try...Catch` bloku, aby przechwycić wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Umieść kod, który może generować wyjątek w `Try` bloku.  
  
     Usuń komentarz z `Dim` wierszy `MsgBox` i, aby wywołać <xref:System.NullReferenceException> wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. W `Catch` bloku Użyj `My.Application.Log.WriteException` metody, aby zapisać informacje o wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Poniższy przykład pokazuje kompletny kod rejestrowania obsługiwanego wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>Aby zarejestrować nieobsłużony wyjątek  
  
1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** wybierz polecenie **Właściwości**.  
  
2. Kliknij kartę **aplikacja** .  
  
3. Kliknij przycisk **Wyświetl zdarzenia aplikacji** , aby otworzyć Edytor kodu.  
  
     Spowoduje to otwarcie pliku ApplicationEvents. vb.  
  
4. Plik ApplicationEvents. vb jest otwarty w edytorze kodu. W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.  
  
5. W menu **deklaracje** wybierz pozycję **UnhandledException**.  
  
     Aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenie przed uruchomieniem aplikacji głównej.  
  
6. Dodaj `My.Application.Log.WriteException` metodę do procedury obsługi `UnhandledException` zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Poniższy przykład pokazuje kompletny kod rejestrowania nieobsłużonego wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
