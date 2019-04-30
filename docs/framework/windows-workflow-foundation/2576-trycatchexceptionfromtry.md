---
title: 2576 — TryCatchExceptionFromTry
ms.date: 03/30/2017
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
ms.openlocfilehash: cdc48a1a08e997f7bc6a0ad6b93aa13640af9ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755652"
---
# <a name="2576---trycatchexceptionfromtry"></a>2576 — TryCatchExceptionFromTry
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|2576|  
|słowa kluczowe|WFActivities|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działania TryCatch złapał wyjątek.  
  
## <a name="message"></a>Komunikat  
 Działania TryCatch "%1" został zgłoszony wyjątek typu "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Wyjątek|xs:String|Nazwa typu wyjątku.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
