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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="652b9-102">Obsługa błędów w działaniach asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="652b9-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="652b9-103">Dostarczanie obsługi błędów w obejmuje <xref:System.Activities.AsyncCodeActivity> routingu błędu za pośrednictwem systemu wywołania zwrotnego działania.</span><span class="sxs-lookup"><span data-stu-id="652b9-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="652b9-104">W tym temacie opisano sposób uzyskania błędu, który jest generowany w operacji asynchronicznie z powrotem do hosta, przy użyciu sendmail próbki działania.</span><span class="sxs-lookup"><span data-stu-id="652b9-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="652b9-105">Zwracanie błędu wyrzuconego w działaniu asynchronistym z powrotem do hosta</span><span class="sxs-lookup"><span data-stu-id="652b9-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="652b9-106">Routing błąd w operacji asynchroniiowej z powrotem do hosta w przykładzie działania SendMail obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="652b9-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="652b9-107">Dodaj właściwość Exception `SendMailAsyncResult` do klasy.</span><span class="sxs-lookup"><span data-stu-id="652b9-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="652b9-108">Skopiuj zgłoszony błąd `SendCompleted` do tej właściwości w programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="652b9-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="652b9-109">Zgłosić wyjątek `EndExecute` w programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="652b9-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="652b9-110">Wynikowy kod jest następujący.</span><span class="sxs-lookup"><span data-stu-id="652b9-110">The resulting code is as follows.</span></span>  
  
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
