---
title: 4201 — EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774364"
---
# <a name="4201---endsqlcommandexecute"></a>4201 — EndSqlCommandExecute
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4201|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że zakończono wykonywanie polecenia SQL.  
  
## <a name="message"></a>Komunikat  
 Kończy wykonywanie polecenia SQL: %1  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Klasy SqlCommand|xs:String|Polecenie SQL, który został wykonany.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
