---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce8b2cd52523d8a2efc94214479ca3c41d2dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 - BufferOutOfOrderMessageNoInstance
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3550|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje, że buforowanego receive nie powiodło się. Operacja zostanie podjęta ponownie, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.  
  
## <a name="message"></a>Komunikat  
 W tej chwili nie można wykonać operacji "%1". Kolejna próba zostanie podjęta, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Nazwa operacji.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
