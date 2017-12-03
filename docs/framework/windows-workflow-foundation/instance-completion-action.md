---
title: "Wystąpienie zakończenia działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a>Wystąpienie zakończenia działania
**Wystąpienia ukończenia akcji** właściwość w magazynie wystąpień przepływu pracy SQL umożliwia określenie, czy dane i metadane wystąpienia przepływu pracy są usuwane z bazy danych trwałości po ukończeniu wystąpienia. Dozwolone wartości dla tej właściwości **DeleteAll** i **DeleteNothing**. Poniższa lista zawiera opis tych opcji:  
  
-   **DeleteAll (ustawienie domyślne).** Jeśli wartość właściwości jest równa DeleteAll, dane i metadane wystąpienia przepływu pracy został usunięty z bazy danych trwałości po ukończeniu wystąpienia.  
  
-   **DeleteNothing.** Jeśli wartość właściwości jest równa DeleteNothing, dane i metadane wystąpienia przepływu pracy jest przechowywana w bazie danych trwałości nawet po zakończeniu wystąpienia.  
  
    > [!CAUTION]
    >  Przechowywanie informacji o stanie wystąpienia po ukończone przyczyny wystąpienia bazy danych trwałości zwiększa się rozmiar. Jak operacje bazy danych, które wykonuje podsystemu trwałości zwiększania rozmiaru bazy danych trwać dłużej, więc należy przeczyścić informacje o stanie wystąpienia z bazy danych trwałości okresowo, aby wykonać na poziomie usług, spełniających użytkownika wymagania związane z wydajnością.
