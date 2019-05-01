---
title: Porównywanie transakcji w modelach COM+ i ServiceModel
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857873"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Porównywanie transakcji w modelach COM+ i ServiceModel
W tym temacie opisano kroki umożliwiające symulować transakcyjnych usług COM + przy użyciu atrybutów Windows Communication Foundation (WCF) <xref:System.ServiceModel> przestrzeń nazw zawiera.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulacja modelu COM + przy użyciu atrybuty elementu ServiceModel  
 W poniższej tabeli porównuje <xref:System.EnterpriseServices.TransactionOption> wyliczenie użyty do utworzenia `EnterpriseServices` transakcji i sposób ich odnoszą się do atrybutów usługi WCF <xref:System.ServiceModel> przestrzeń nazw zawiera.  
  
|Atrybut modelu COM +|Atrybuty usługi WCF|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> ustawiono <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `true`.<br /><br /> `TransactionFlow` Atrybutu w elemencie powiązania jest `false`.|  
|Wymagane|<xref:System.ServiceModel.TransactionFlowAttribute> ustawiono <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `true`.<br /><br /> `TransactionFlow` Atrybutu w elemencie powiązania jest `true`.|  
|Obsługiwane|Nie ma bezpośredniego odpowiednika. Ogólnie rzecz biorąc, należy przyjąć nieaktywności dla `Required` zamiast tego.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest `false`.<br /><br /> `TransactionFlow` Atrybutu w elemencie powiązania jest `false`.|  
|Wyłączone|Nie ma bezpośredniego odpowiednika. Ogólnie rzecz biorąc, należy przyjąć nieaktywności dla `NotSupported` zamiast tego.|
