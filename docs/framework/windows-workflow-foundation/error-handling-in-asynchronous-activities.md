---
title: "Obsługa błędów w asynchronicznej działań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7606aeeeb3e2e583f9a217b78bcae4aebc6d8662
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-in-asynchronous-activities"></a>Obsługa błędów w asynchronicznej działań
Zapewnianie obsługi błędów w <xref:System.Activities.AsyncCodeActivity> obejmuje routingu błąd za pomocą działania systemu wywołania zwrotnego. W tym temacie opisano występuje błąd jest zgłaszany w operację asynchroniczną do hosta, za pomocą SendMail przykładowe działanie.  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>Zwróci błąd zgłoszony w działaniu asynchroniczne do hosta  
 Routing błąd w operacji asynchronicznej do hosta w przykładowym działania SendMail obejmuje następujące kroki:  
  
-   Dodaj właściwość wyjątku do `SendMailAsyncResult` klasy.  
  
-   Kopiuj element zgłaszany błąd do tej właściwości w `SendCompleted` obsługi zdarzeń.  
  
-   Zgłoszenie wyjątku `EndExecute` obsługi zdarzeń.  
  
 Wynikowy kod ma następującą składnię.  
  
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
