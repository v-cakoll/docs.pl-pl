---
title: 'Instrukcje: rejestrowanie komunikatów podczas uruchamiania lub zamykania aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: ac5fb17e527bcbcb55f98ec0ced06c152555ce6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410078"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)

Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o zdarzeniach występujących w aplikacji. Ten przykład pokazuje, jak używać `My.Application.Log.WriteEntry` metody ze `Startup` `Shutdown` zdarzeniami i, aby pisać informacje o śledzeniu.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Aby uzyskać dostęp do kodu programu obsługi zdarzeń aplikacji  
  
1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** wybierz polecenie **Właściwości**.  
  
2. Kliknij kartę **aplikacja** .  
  
3. Kliknij przycisk **Wyświetl zdarzenia aplikacji** , aby otworzyć Edytor kodu.  
  
     Spowoduje to otwarcie pliku ApplicationEvents. vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Aby rejestrować komunikaty podczas uruchamiania aplikacji  
  
1. Plik ApplicationEvents. vb jest otwarty w edytorze kodu. W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.  
  
2. W menu **deklaracje** wybierz pozycję **Uruchamianie**.  
  
     Aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzenie przed uruchomieniem aplikacji głównej.  
  
3. Dodaj `My.Application.Log.WriteEntry` metodę do `Startup` procedury obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Aby rejestrować komunikaty podczas zamykania aplikacji  
  
1. Plik ApplicationEvents. vb jest otwarty w edytorze kodu. W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.  
  
2. W menu **deklaracje** wybierz pozycję **Zamknij**.  
  
     Aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzenie po uruchomieniu aplikacji głównej, ale przed jej zamknięciem.  
  
3. Dodaj `My.Application.Log.WriteEntry` metodę do `Shutdown` procedury obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Przykład  

 Możesz użyć **projektanta projektu** , aby uzyskać dostęp do zdarzeń aplikacji w edytorze kodu. Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Praca z dziennikami aplikacji](working-with-application-logs.md)
