---
title: 3502 — InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756094"
---
# <a name="3502---inferredoperationdescription"></a>3502 — InferredOperationDescription
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3502|  
|słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że obiekt OperationDescription została wykryta z WorkflowService.  
  
## <a name="message"></a>Komunikat  
 Obiekt OperationDescription o nazwie = "%1" w kontrakcie "%2" została wykryta z WorkflowService. IsOneWay=%3.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Nazwa operacji.|  
|ContractName|xs:String|Nazwa kontraktu.|  
|IsOneWay|xs:String|Wartość PRAWDA lub Fałsz wskazująca, czy kontrakt jest jednokierunkowa.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
