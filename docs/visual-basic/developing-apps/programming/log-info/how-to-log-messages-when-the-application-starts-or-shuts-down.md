---
title: 'Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 80b07e67cb307d461e63df9f94c9d0962eb6374a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588898"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)
Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji. Ten przykład przedstawia sposób użycia `My.Application.Log.WriteEntry` metody z `Startup` i `Shutdown` zdarzeń w celu zapisania informacji śledzenia.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Dostęp do kodu obsługi zdarzeń aplikacji  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, wybierz **właściwości**.  
  
2.  Kliknij przycisk **aplikacji** kartę.  
  
3.  Kliknij przycisk **Wyświetl zdarzenia aplikacji** przycisk, aby otworzyć edytora kodu.  
  
     Spowoduje to otwarcie pliku ApplicationEvents.vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Aby rejestrowanie wiadomości podczas uruchamiania aplikacji  
  
1.  ApplicationEvents.vb plik zostać otwarty w edytorze kodu. Na **ogólne** menu, wybierz **zdarzenia moja_aplikacja**.  
  
2.  Na **deklaracje** menu, wybierz **uruchamiania**.  
  
     Generuje aplikacji <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń przed uruchomieniem aplikacji głównej.  
  
3.  Dodaj `My.Application.Log.WriteEntry` metodę `Startup` obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Aby rejestrowanie wiadomości podczas zamykania aplikacji  
  
1.  ApplicationEvents.vb plik zostać otwarty w edytorze kodu. Na **ogólne** menu, wybierz **zdarzenia moja_aplikacja**.  
  
2.  Na **deklaracje** menu, wybierz **zamknięcia**.  
  
     Generuje aplikacji <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń po uruchomieniu aplikacji głównej, ale przed jego zamknięciem.  
  
3.  Dodaj `My.Application.Log.WriteEntry` metodę `Shutdown` obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a>Przykład  
 Można użyć **projektanta projektu** do zdarzeń aplikacji w edytorze kodu dostępu. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
