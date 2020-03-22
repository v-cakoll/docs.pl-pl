---
title: 'Porady: wyjątki rejestru'
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

Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o wyjątkach, które występują w aplikacji. Te przykłady pokazują, `My.Application.Log.WriteException` jak używać metody do rejestrowania wyjątków, które można przechwyć jawnie i wyjątki, które są nieobsługiwał.  
  
 Aby rejestrować informacje o `My.Application.Log.WriteEntry` śledzeniu, użyj metody. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>Aby zarejestrować obsługiwany wyjątek  
  
1. Utwórz metodę, która wygeneruje informacje o wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Użyj `Try...Catch` bloku, aby przechwyć wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Umieść kod, który może wygenerować wyjątek w `Try` bloku.  
  
     `Dim` Odkomentuj `MsgBox` wiersze <xref:System.NullReferenceException> i spowodować wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. W `Catch` bloku użyj `My.Application.Log.WriteException` metody, aby zapisać informacje o wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     W poniższym przykładzie przedstawiono pełny kod do rejestrowania obsługiwanego wyjątku.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>Aby zarejestrować nieobsługiwalny wyjątek  
  
1. Wybierz projekt w **Eksploratorze rozwiązań**. W menu **Projekt** wybierz polecenie **Właściwości**.  
  
2. Kliknij kartę **Aplikacja.**  
  
3. Kliknij przycisk **Wyświetl zdarzenia aplikacji,** aby otworzyć Edytor kodu.  
  
     Spowoduje to otwarcie pliku ApplicationEvents.vb.  
  
4. Otwórz plik ApplicationEvents.vb w Edytorze kodu. W menu **Ogólne** wybierz polecenie **MyApplication Events**.  
  
5. W menu **Deklaracje** wybierz polecenie **UnhandledException**.  
  
     Aplikacja wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenie przed uruchomieniu aplikacji głównej.  
  
6. Dodaj `My.Application.Log.WriteException` metodę do `UnhandledException` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     W poniższym przykładzie przedstawiono pełny kod do rejestrowania nieobsługiwał wyjątek.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Porady: zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
