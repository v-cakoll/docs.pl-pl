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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 712f8a7a153d7255275ff7ebaa647d5a624f8ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
