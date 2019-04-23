---
title: Inny dziennika zdarzeń została już zarejestrowana źródło o tej nazwie
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: d932869504b2d8a5f3a948b190e5528bfcfa664f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314675"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Inny dziennika zdarzeń została już zarejestrowana źródło o tej nazwie
Nastąpiła próba zapisu do dziennika zdarzeń, gdzie określona źródłowa jest zarejestrowany w innym dzienniku zdarzeń.  
  
 Należy ustawić <xref:System.Diagnostics.EventLog.Source%2A> właściwości usługi <xref:System.Diagnostics.EventLog> wystąpienie składnika przed składnika zapisuje wpis dziennika. W takim przypadku system sprawdza, czy określone źródło jest zarejestrowany w dzienniku zdarzeń, do którego jest pisanie składnika i wywołania <xref:System.Diagnostics.EventLog.CreateEventSource%2A> w razie potrzeby.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Usuń skojarzenie źródła z pierwszym przy użyciu dziennika <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> lub <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> metody.  
  
2. Zarejestruj nowy dziennik źródła.  
  
## <a name="see-also"></a>Zobacz także

- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
