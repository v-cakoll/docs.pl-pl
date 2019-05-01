---
title: 1037 — RuntimeTransactionComplete
ms.date: 03/30/2017
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
ms.openlocfilehash: 7a94c917157904c5cb84105c41842657a534c973
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924296"
---
# <a name="1037---runtimetransactioncomplete"></a>1037 — RuntimeTransactionComplete
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1037|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że transakcja środowiska uruchomieniowego została zakończona.  
  
## <a name="message"></a>Komunikat  
 Transakcja środowiska uruchomieniowego została ukończona ze stanem "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Stan|xs:String|Stan transakcji.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
