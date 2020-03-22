---
title: 'Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 5a4ef3888ba8371d26204c3569b5fb9bae1f15f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352097"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)

Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji. W tym przykładzie `My.Application.Log.WriteEntry` pokazano, `Startup` jak `Shutdown` używać metody z i zdarzeń do zapisu informacji śledzenia.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Aby uzyskać dostęp do kodu obsługi zdarzeń aplikacji  
  
1. Wybierz projekt w **Eksploratorze rozwiązań**. W menu **Projekt** wybierz polecenie **Właściwości**.  
  
2. Kliknij kartę **Aplikacja.**  
  
3. Kliknij przycisk **Wyświetl zdarzenia aplikacji,** aby otworzyć Edytor kodu.  
  
     Spowoduje to otwarcie pliku ApplicationEvents.vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Aby rejestrować komunikaty po uruchomieniu aplikacji  
  
1. Otwórz plik ApplicationEvents.vb w Edytorze kodu. W menu **Ogólne** wybierz polecenie **MyApplication Events**.  
  
2. W menu **Deklaracje** wybierz polecenie **Uruchamianie**.  
  
     Aplikacja wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzenie przed uruchomieniu aplikacji głównej.  
  
3. Dodaj `My.Application.Log.WriteEntry` metodę do `Startup` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Aby rejestrować komunikaty po zamknięciu aplikacji  
  
1. Otwórz plik ApplicationEvents.vb w Edytorze kodu. W menu **Ogólne** wybierz polecenie **MyApplication Events**.  
  
2. W menu **Deklaracje** wybierz polecenie **Zamknięcie**.  
  
     Aplikacja wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzenie po uruchomieniu głównej aplikacji, ale przed zamknięciem.  
  
3. Dodaj `My.Application.Log.WriteEntry` metodę do `Shutdown` programu obsługi zdarzeń.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Przykład  

 **Projektantprojektu** można użyć, aby uzyskać dostęp do zdarzeń aplikacji w Edytorze kodu. Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
