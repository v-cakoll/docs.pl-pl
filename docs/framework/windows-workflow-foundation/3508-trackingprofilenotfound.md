---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512187"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3508|  
|Słowa kluczowe|WFServices|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Oznacza TrackingProfile nie został znaleziony w pliku konfiguracji lub obiekt ActivityDefinitionId jest niezgodny z profilu.  
  
## <a name="message"></a>Komunikat  
 TrackingProfile "%1" dla obiektu ActivityDefinitionId "%2" nie można odnaleźć. Nie można odnaleźć TrackingProfile w pliku konfiguracji, albo obiekt ActivityDefinitionId jest niezgodny.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:String|Nazwa profilu śledzenia.|  
|Obiekt ActivityDefinitionId|xs:String|Identyfikator definicji działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
