---
title: 4208 — RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774299"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a>4208 — RetryingSqlCommandDueToSqlError
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4208|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że dostawcy bazy danych SQL jest ponowieniem uruchomienia polecenia SQL z powodu błędu SQL.  
  
## <a name="message"></a>Komunikat  
 Ponawianie próby za pomocą polecenia SQL ze względu na %1. numer błędu SQL.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ErrorNumber|xs:String|Numer błędu SQL.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
