---
title: 'Porady: wyjątki rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352084"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Porady: wyjątki rejestru w Visual Basic

Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o wyjątkach występujących w aplikacji. W poniższych przykładach pokazano, jak za pomocą metody `My.Application.Log.WriteException` rejestrować wyjątki, które zostały wyszukane jawnie i wyjątki, które nie są obsługiwane.  
  
 Aby uzyskać informacje o śledzeniu rejestrowania, użyj metody `My.Application.Log.WriteEntry`. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>Aby zarejestrować obsłużony wyjątek  
  
1. Utwórz metodę, która będzie generować informacje o wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Użyj bloku `Try...Catch`, aby przechwycić wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Umieść kod, który może generować wyjątek w bloku `Try`.  
  
     Usuń komentarz z `Dim` i `MsgBox` wierszy, aby spowodować <xref:System.NullReferenceException> wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. W bloku `Catch` Użyj metody `My.Application.Log.WriteException`, aby zapisać informacje o wyjątku.  
  
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
  
     Aplikacja zgłasza zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> przed uruchomieniem aplikacji głównej.  
  
6. Dodaj metodę `My.Application.Log.WriteException` do procedury obsługi zdarzeń `UnhandledException`.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Poniższy przykład pokazuje kompletny kod rejestrowania nieobsłużonego wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Instrukcje: zapisywanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
