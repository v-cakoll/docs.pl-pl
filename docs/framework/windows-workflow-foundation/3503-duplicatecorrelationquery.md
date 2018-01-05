---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 997bdf4423364e9b5361635820849a6bde9e8960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="3503---duplicatecorrelationquery"></a>3503 - DuplicateCorrelationQuery
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3503|  
|Słowa kluczowe|WFServices|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje, że znaleziono zduplikowane CorrelationQuery. Zduplikowane zapytanie nie zostanie użyte, podczas obliczania korelacji.  
  
## <a name="message"></a>Komunikat  
 Znaleziono zduplikowane CorrelationQuery o Where = '%1'. To zduplikowane zapytanie nie zostanie użyte podczas obliczania korelacji.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Gdzie|xs:String|Gdzie część zapytania korelacji.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
