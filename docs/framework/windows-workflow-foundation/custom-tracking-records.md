---
title: "Śledzenie niestandardowych rekordów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5202f69ac3f5408091d73f2ae39f92659a991740
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-tracking-records"></a>Śledzenie niestandardowych rekordów
W tym temacie przedstawiono sposób tworzenia niestandardowych śledzenie rekordów i wypełnić je danymi być emitowane wraz z rekordów.  
  
## <a name="emitting-custom-tracking-records"></a>Emitowanie śledzenia niestandardowych rekordów  
 Niestandardowe śledzenie rekordów może być wysyłany z działania kodu, jak pokazano w poniższym przykładzie.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 A <xref:System.Activities.Tracking.CustomTrackingRecord> emitowanego działania kodu, wywołując <xref:System.Activities.NativeActivityContext.Track%2A> metoda `ActvityContext`.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Server AppFabric monitorowania](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorowanie aplikacji przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
