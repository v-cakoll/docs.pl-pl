---
title: 451 — MessageLogInfo
ms.date: 03/30/2017
ms.assetid: 485b4b29-dc21-4a35-93f8-5f4726d6aa5a
ms.openlocfilehash: e61ef49b947e59f65933f6cbf3ba6b8669aa3bba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757693"
---
# <a name="451---messageloginfo"></a>451 — MessageLogInfo
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|451|  
|słowa kluczowe|Rozwiązywanie problemów, WCFMessageLogging|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, gdy informacje dziennika komunikatów są wysyłane.  
  
## <a name="message"></a>Komunikat  
 %1  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|data1|`xs:string`||  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
