---
title: Porównywanie transakcji w modelach COM+ i ServiceModel
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488650"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Porównywanie transakcji w modelach COM+ i ServiceModel
W tym temacie omówiono sposób symulować transakcyjnych usług COM + przy użyciu atrybutów Windows Communication Foundation (WCF) <xref:System.ServiceModel> zawiera przestrzeń nazw.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulowanie COM + przy użyciu atrybuty elementu ServiceModel  
 W poniższej tabeli porównuje <xref:System.EnterpriseServices.TransactionOption> używany do tworzenia wyliczenia `EnterpriseServices` transakcji i sposób grupowania atrybutów WCF <xref:System.ServiceModel> zawiera przestrzeń nazw.  
  
|Atrybut modelu COM +|Atrybuty WCF|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> ustawiono <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `true`.<br /><br /> `TransactionFlow` w elemencie powiązania jest `false`.|  
|Wymagane|<xref:System.ServiceModel.TransactionFlowAttribute> ustawiono <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `true`.<br /><br /> `TransactionFlow` w elemencie powiązania jest `true`.|  
|Obsługiwane|Nie ma odpowiednika bezpośredniego. Ogólnie rzecz biorąc, powinna przyjąć zachowania nieaktywności `Required` zamiast tego.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `false`.<br /><br /> `TransactionFlow` w elemencie powiązania jest `false`.|  
|Wyłączone|Nie ma odpowiednika bezpośredniego. Ogólnie rzecz biorąc, powinna przyjąć zachowania nieaktywności `NotSupported` zamiast tego.|
