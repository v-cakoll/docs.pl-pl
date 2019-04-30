---
title: 2577 — TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755626"
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 — TryCatchExceptionDuringCancelation
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|2577|  
|słowa kluczowe|WFActivities|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie podrzędne działania TryCatch został zgłoszony wyjątek w trakcie anulowania.  
  
## <a name="message"></a>Komunikat  
 Działanie podrzędne działania TryCatch '%1' został zgłoszony wyjątek w trakcie anulowania.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
