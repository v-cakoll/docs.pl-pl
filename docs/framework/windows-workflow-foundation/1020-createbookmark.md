---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510462"
---
# <a name="1020---createbookmark"></a>1020 - CreateBookmark
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1020|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że utworzono zakładkę dla działania.  
  
## <a name="message"></a>Komunikat  
 Utworzono zakładkę dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.  Nazwa zakładki: %4, zakres zakładek: %5.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Działanie|xs:String|Nazwa typu działania.|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Identyfikator wystąpienia|xs:String|Identyfikator wystąpienia działania.|  
|Nazwa zakładki|xs:String|Nazwa zakładki.|  
|Zakres zakładek|xs:String|Zakres zakładki.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
