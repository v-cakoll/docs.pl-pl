---
title: 'Punkt końcowy: Błędne sesje komunikacji niezawodnej na sekundę'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 198acbeff6b8a54dcc6e4ae6966fea996da4b745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472774"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Punkt końcowy: Błędne sesje komunikacji niezawodnej na sekundę
Nazwa licznika: Błędne sesje komunikacji niezawodnej na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba sesji komunikacji niezawodnej z błędami są w tym punkcie końcowym na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
