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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a459e6df0e030f4e17bb73461d8fa790a61787e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
