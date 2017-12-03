---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 144ab1a4a2fd313dc7817846e3e0118145cd3f8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3502|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje, że OperationDescription został wywnioskowany na podstawie obiektu WorkflowService.  
  
## <a name="message"></a>Komunikat  
 OperationDescription o nazwie "% 1" w kontrakcie "%2" został wywnioskowany na podstawie obiektu WorkflowService. Ustawienie właściwości IsOneWay = %3.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Nazwa operacji.|  
|ContractName|xs:String|Nazwa kontraktu.|  
|Ustawienie właściwości IsOneWay|xs:String|Wartość PRAWDA lub Fałsz wskazująca, czy kontrakt jest jednokierunkowa.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
