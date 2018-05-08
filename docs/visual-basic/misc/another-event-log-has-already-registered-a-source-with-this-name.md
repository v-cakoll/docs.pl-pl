---
title: Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: b12fd5dcdeaccb0dc294c44e4b8a898726978633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Inny dziennik zdarzeń zarejestrowała już źródło o tej nazwie
Podjęto próbę zapisu do dziennika zdarzeń gdzie określone źródło jest zarejestrowany w innym dziennika zdarzeń.  
  
 Należy ustawić <xref:System.Diagnostics.EventLog.Source%2A> właściwości użytkownika <xref:System.Diagnostics.EventLog> wystąpienie składnika przed składnika dokona wpisu w dzienniku. W takim przypadku system sprawdza, czy określone źródło jest zarejestrowana z dziennika zdarzeń, do którego jest pisanie składnika i wywołania <xref:System.Diagnostics.EventLog.CreateEventSource%2A> w razie potrzeby.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń skojarzenie źródła przy pierwszym użyciu dziennika <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> lub <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.  
  
2.  Zarejestruj źródło nowy dziennik.  
  
## <a name="see-also"></a>Zobacz też  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

