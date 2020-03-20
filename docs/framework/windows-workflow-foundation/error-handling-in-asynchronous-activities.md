---
title: Obsługa błędów w działaniach asynchronicznych
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: c63ce231687b03bdba57edd38c32270eabeff834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182953"
---
# <a name="error-handling-in-asynchronous-activities"></a>Obsługa błędów w działaniach asynchronicznych
Dostarczanie obsługi błędów w obejmuje <xref:System.Activities.AsyncCodeActivity> routingu błędu za pośrednictwem systemu wywołania zwrotnego działania. W tym temacie opisano sposób uzyskania błędu, który jest generowany w operacji asynchronicznie z powrotem do hosta, przy użyciu sendmail próbki działania.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Zwracanie błędu wyrzuconego w działaniu asynchronistym z powrotem do hosta  
 Routing błąd w operacji asynchroniiowej z powrotem do hosta w przykładzie działania SendMail obejmuje następujące kroki:  
  
- Dodaj właściwość Exception `SendMailAsyncResult` do klasy.  
  
- Skopiuj zgłoszony błąd `SendCompleted` do tej właściwości w programie obsługi zdarzeń.  
  
- Zgłosić wyjątek `EndExecute` w programie obsługi zdarzeń.  
  
 Wynikowy kod jest następujący.  
  
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
