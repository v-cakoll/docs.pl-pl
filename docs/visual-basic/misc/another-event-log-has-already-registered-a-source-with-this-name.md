---
title: "Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie
Podjęto próbę zapisu do dziennika zdarzeń gdzie określone źródło jest zarejestrowany w innym dziennika zdarzeń.  
  
 Należy ustawić <xref:System.Diagnostics.EventLog.Source%2A> właściwości użytkownika <xref:System.Diagnostics.EventLog> wystąpienie składnika przed składnika dokona wpisu w dzienniku. W takim przypadku system sprawdza, czy określone źródło jest zarejestrowana z dziennika zdarzeń, do którego jest pisanie składnika i wywołania <xref:System.Diagnostics.EventLog.CreateEventSource%2A> w razie potrzeby.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń skojarzenie źródła przy pierwszym użyciu dziennika <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> lub <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.  
  
2.  Zarejestruj źródło nowy dziennik.  
  
## <a name="see-also"></a>Zobacz też  
 [My.Application.log — obiekt](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [Porady: usuwanie źródłem zdarzenia](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [Porady: Dodawanie aplikacji jako źródło wpisów dziennika zdarzeń](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
