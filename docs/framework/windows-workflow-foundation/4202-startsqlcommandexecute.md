---
title: 4202 — StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774377"
---
# <a name="4202---startsqlcommandexecute"></a>4202 — StartSqlCommandExecute
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4202|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że jest wykonywana za pomocą polecenia SQL.  
  
## <a name="message"></a>Komunikat  
 Rozpoczynanie wykonywania polecenia SQL: %1  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Klasy SqlCommand|xs:String|Polecenie SQL, który został wykonany.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
