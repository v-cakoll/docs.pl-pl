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
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="393d3-102">Obsługa błędów w działaniach asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="393d3-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="393d3-103">Zapewnianie obsługi błędów w <xref:System.Activities.AsyncCodeActivity> obejmuje routingu błąd za pośrednictwem systemu wywołania zwrotnego tego działania.</span><span class="sxs-lookup"><span data-stu-id="393d3-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="393d3-104">W tym temacie opisano sposób wystąpi błąd, który jest generowany w operacji asynchronicznej powrotem do hosta przy użyciu przykładu działanie SendMail.</span><span class="sxs-lookup"><span data-stu-id="393d3-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="393d3-105">Zwraca błąd zgłoszony w działaniu asynchronicznego powrotem do hosta</span><span class="sxs-lookup"><span data-stu-id="393d3-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="393d3-106">Routing błąd w operacji asynchronicznej do hosta w przykładzie działanie SendMail obejmuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="393d3-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="393d3-107">Dodaj właściwość wyjątku do `SendMailAsyncResult` klasy.</span><span class="sxs-lookup"><span data-stu-id="393d3-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="393d3-108">Skopiuj zgłoszonego błędu do tej właściwości w `SendCompleted` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="393d3-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="393d3-109">Zgłoszenie wyjątku `EndExecute` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="393d3-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="393d3-110">Następnie kod wynikowy jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="393d3-110">The resulting code is as follows.</span></span>  
  
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
