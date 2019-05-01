---
title: 4203 — RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774351"
---
# <a name="4203---renewlocksystemerror"></a>4203 — RenewLockSystemError
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4203|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje dostawcy bazy danych SQL nie udało się rozszerzyć wygaśnięcia blokady z powodu wygaśnięcia blokady, albo już minęła lub właściciel blokady został usunięty. SqlWorkflowInstanceStore zostanie przerwane.  
  
## <a name="message"></a>Komunikat  
 Nie można rozszerzyć wygaśnięcia blokady, wygaśnięcia blokady już przekazany lub właściciel blokady został usunięty. Aborting SqlWorkflowInstanceStore.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
