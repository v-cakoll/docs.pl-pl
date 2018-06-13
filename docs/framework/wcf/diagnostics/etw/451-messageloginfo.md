---
title: 451 — MessageLogInfo
ms.date: 03/30/2017
ms.assetid: 485b4b29-dc21-4a35-93f8-5f4726d6aa5a
ms.openlocfilehash: e61ef49b947e59f65933f6cbf3ba6b8669aa3bba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33467812"
---
# <a name="451---messageloginfo"></a>451 — MessageLogInfo
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|451|  
|Słowa kluczowe|Rozwiązywanie problemów, WCFMessageLogging|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany po wysłaniu wiadomości informacji dziennika.  
  
## <a name="message"></a>Komunikat  
 %1  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|dane1|`xs:string`||  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
