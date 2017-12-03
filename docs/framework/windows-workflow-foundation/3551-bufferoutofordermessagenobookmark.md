---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc505a4e0e79b37f9adff41b80dcba55215576f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3551|  
|Słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje, że nie powiodło się wznowienie zakładki. Buforowany operacji odbierania zostanie podjęta ponownie gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.  
  
## <a name="message"></a>Komunikat  
 W tej chwili nie można wykonać operacji "%2" dla wystąpienia usługi "%1". Kolejna próba zostanie podjęta, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Nazwa operacji.|  
|ServiceInstanceId|xs:String|Identyfikator wystąpienia usługi.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
