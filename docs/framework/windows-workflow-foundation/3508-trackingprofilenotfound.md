---
title: 3508 — TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755574"
---
# <a name="3508---trackingprofilenotfound"></a>3508 — TrackingProfileNotFound
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3508|  
|słowa kluczowe|WFServices|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Oznacza TrackingProfile nie znajduje się w pliku konfiguracji lub ActivityDefinitionId nie pasuje do profilu.  
  
## <a name="message"></a>Komunikat  
 TrackingProfile "%1" dla ActivityDefinitionId "%2" nie można odnaleźć. TrackingProfile nie znajduje się w pliku konfiguracji, albo ActivityDefinitionId jest niezgodny.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:String|Nazwa profilu śledzenia.|  
|ActivityDefinitionId|xs:String|Identyfikator definicji działania.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
