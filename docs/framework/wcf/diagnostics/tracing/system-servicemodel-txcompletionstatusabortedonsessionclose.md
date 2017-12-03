---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 695ebb2089147093601f2d51f11f11ca45861590
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a>System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
Określona transakcja została przerwana, ponieważ była niezakończona podczas zamykania sesji i TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute została ustawiona na false.  
  
## <a name="description"></a>Opis  
 Śledzone, jeśli bieżąca aktywna sesja została zamknięta i transakcja nie została ukończona, a ma ustawioną wartość TransactionAutoCompleteOnSessionClose `false`.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Ślad wskazuje potencjalnych błędów aplikacji, które należy zbadać.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
