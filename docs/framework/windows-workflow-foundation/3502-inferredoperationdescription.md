---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512008"
---
# <a name="3502---inferredoperationdescription"></a>3502 - InferredOperationDescription
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3502|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
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
