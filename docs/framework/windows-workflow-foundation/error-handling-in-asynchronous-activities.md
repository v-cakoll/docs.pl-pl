---
title: Obsługa błędów w asynchronicznej działań
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 4a7cbecef596eec6eaa128b8ffc7bc5c6e4b79bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="6f9bb-102">Obsługa błędów w asynchronicznej działań</span><span class="sxs-lookup"><span data-stu-id="6f9bb-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="6f9bb-103">Zapewnianie obsługi błędów w <xref:System.Activities.AsyncCodeActivity> obejmuje routingu błąd za pomocą działania systemu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6f9bb-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="6f9bb-104">W tym temacie opisano występuje błąd jest zgłaszany w operację asynchroniczną do hosta, za pomocą SendMail przykładowe działanie.</span><span class="sxs-lookup"><span data-stu-id="6f9bb-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="6f9bb-105">Zwróci błąd zgłoszony w działaniu asynchroniczne do hosta</span><span class="sxs-lookup"><span data-stu-id="6f9bb-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="6f9bb-106">Routing błąd w operacji asynchronicznej do hosta w przykładowym działania SendMail obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="6f9bb-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="6f9bb-107">Dodaj właściwość wyjątku do `SendMailAsyncResult` klasy.</span><span class="sxs-lookup"><span data-stu-id="6f9bb-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="6f9bb-108">Kopiuj element zgłaszany błąd do tej właściwości w `SendCompleted` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6f9bb-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="6f9bb-109">Zgłoszenie wyjątku `EndExecute` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6f9bb-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="6f9bb-110">Wynikowy kod ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="6f9bb-110">The resulting code is as follows.</span></span>  
  
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
