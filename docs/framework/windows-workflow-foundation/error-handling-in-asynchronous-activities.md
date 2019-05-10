---
title: Obsługa błędów w działaniach asynchronicznych
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 7a1db144e4738870d3ff5fe68df11b2fb06ef3d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640959"
---
# <a name="error-handling-in-asynchronous-activities"></a>Obsługa błędów w działaniach asynchronicznych
Zapewnianie obsługi błędów w <xref:System.Activities.AsyncCodeActivity> obejmuje routingu błąd za pośrednictwem systemu wywołania zwrotnego tego działania. W tym temacie opisano sposób wystąpi błąd, który jest generowany w operacji asynchronicznej powrotem do hosta przy użyciu przykładu działanie SendMail.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Zwraca błąd zgłoszony w działaniu asynchronicznego powrotem do hosta  
 Routing błąd w operacji asynchronicznej do hosta w przykładzie działanie SendMail obejmuje następujące czynności:  
  
- Dodaj właściwość wyjątku do `SendMailAsyncResult` klasy.  
  
- Skopiuj zgłoszonego błędu do tej właściwości w `SendCompleted` programu obsługi zdarzeń.  
  
- Zgłoszenie wyjątku `EndExecute` programu obsługi zdarzeń.  
  
 Następnie kod wynikowy jest w następujący sposób.  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }   
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;   
        }  
    }  
```
