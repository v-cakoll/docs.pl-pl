---
title: 4209 — TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774273"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 — TimeoutOpeningSqlConnection
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4209|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że limit czasu podczas próby otwarcia połączenia SQL.  
  
## <a name="message"></a>Komunikat  
 Limit czasu podczas próby otwarcia połączenia SQL. Operacja nie została ukończona w ciągu przydzielonego limitu czasu %1. Czas przydzielony na tę operację mógł stanowić część większego limitu czasu.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|limit czasu|xs:String|Limit czasu otwierania połączenia SQL.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
