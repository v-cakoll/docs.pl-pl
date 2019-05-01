---
title: 440 — StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 4b2b6b0fa9df4725edd4929512eb1d7534d933b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774174"
---
# <a name="440---startsignpostevent1"></a>440 — StartSignpostEvent1
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|440|  
|słowa kluczowe|Rozwiązywanie problemów|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 W śledzenie aktywności wskazuje, czy wiadomość została uruchomiona przekraczania granicy działania w wysyłać ani odbierać.  
  
## <a name="message"></a>Komunikat  
 Hranice aktivity  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ExtendedData|`xs:string`|Nazwa działania.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
