---
title: "Porównywanie transakcji w modelach COM+ i ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Porównywanie transakcji w modelach COM+ i ServiceModel
W tym temacie omówiono sposób symulować transakcyjne COM + usługi za pomocą [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] atrybuty <xref:System.ServiceModel> zawiera przestrzeń nazw.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulowanie COM + przy użyciu atrybuty elementu ServiceModel  
 W poniższej tabeli porównuje <xref:System.EnterpriseServices.TransactionOption> używany do tworzenia wyliczenia `EnterpriseServices` transakcji i sposób ich skorelowany [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atrybuty <xref:System.ServiceModel> przestrzeń nazw zawiera.  
  
|Atrybut modelu COM +|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]atrybuty|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute>ustawiono <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>jest `true`.<br /><br /> `TransactionFlow` w elemencie powiązania jest `false`.|  
|Wymagane|<xref:System.ServiceModel.TransactionFlowAttribute>ustawiono <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>jest `true`.<br /><br /> `TransactionFlow` w elemencie powiązania jest `true`.|  
|Obsługiwane|Nie ma odpowiednika bezpośredniego. Ogólnie rzecz biorąc, powinna przyjąć zachowania nieaktywności `Required` zamiast tego.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>jest `false`.<br /><br /> `TransactionFlow` w elemencie powiązania jest `false`.|  
|Wyłączone|Nie ma odpowiednika bezpośredniego. Ogólnie rzecz biorąc, powinna przyjąć zachowania nieaktywności `NotSupported` zamiast tego.|
