---
title: 4212 — LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774221"
---
# <a name="4212---lockretrytimeout"></a>4212 — LockRetryTimeout
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4212|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Dostawcy bazy danych SQL został przekroczony limit czasu, próbując uzyskać blokadę wystąpienia.  
  
## <a name="message"></a>Komunikat  
 Limit czasu, próbując uzyskać blokadę wystąpienia.  Operacja nie została ukończona w ciągu przydzielonego limitu czasu %1. Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Opóźnienie|xs:String|Opóźnienie między ponownymi próbami.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
