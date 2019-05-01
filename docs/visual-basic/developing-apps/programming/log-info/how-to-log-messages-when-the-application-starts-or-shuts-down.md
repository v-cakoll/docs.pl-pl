---
title: 'Instrukcje: Komunikaty dziennika podczas uruchamiania aplikacji lub zamknięciu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 8fc7b441c6e19d70ceefa3422cf9823007280b64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052498"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Instrukcje: Komunikaty dziennika podczas uruchamiania aplikacji lub zamknięciu (Visual Basic)
Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym przykładzie pokazano, jak używać `My.Application.Log.WriteEntry` metody z `Startup` i `Shutdown` zdarzenia do zapisania informacji śledzenia.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Dostęp do kodu programu obsługi zdarzeń aplikacji  
  
1. Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz **właściwości**.  
  
2. Kliknij przycisk **aplikacji** kartę.  
  
3. Kliknij przycisk **Wyświetl zdarzenia aplikacji** przycisk, aby otworzyć Edytor kodu.  
  
     Spowoduje to otwarcie pliku ApplicationEvents.vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Umożliwiają rejestrowanie wiadomości podczas uruchamiania aplikacji  
  
1. ApplicationEvents.vb plik zostać otwarty w edytorze kodu. Na **ogólne** menu, wybierz **zdarzenia MojaAplikacja**.  
  
2. Na **deklaracje** menu, wybierz **uruchamiania**.  
  
     Wywołuje aplikację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń przed uruchomieniem aplikacji głównej.  
  
3. Dodaj `My.Application.Log.WriteEntry` metody `Startup` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Aby rejestrowanie wiadomości podczas zamykania aplikacji  
  
1. ApplicationEvents.vb plik zostać otwarty w edytorze kodu. Na **ogólne** menu, wybierz **zdarzenia MojaAplikacja**.  
  
2. Na **deklaracje** menu, wybierz **zamknięcia**.  
  
     Wywołuje aplikację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń po uruchomień aplikacji głównej, ale przed jego zamknięciem.  
  
3. Dodaj `My.Application.Log.WriteEntry` metody `Shutdown` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Przykład  
 Możesz użyć **projektanta projektu** można uzyskiwać dostęp do zdarzeń aplikacji w edytorze kodu. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
