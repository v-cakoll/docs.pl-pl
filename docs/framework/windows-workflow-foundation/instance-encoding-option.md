---
title: "Opcja kodowania wystąpienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7664eecb68ff9aec0f5e3e31aa08058700f0e92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="instance-encoding-option"></a>Opcja kodowania wystąpienia
**Opcji kodowanie wystąpienia** właściwość w magazynie wystąpień przepływu pracy SQL umożliwia określenie, czy dostawca trwałości SQL należy skompresować informacji stanu wystąpienia przepływu pracy przy użyciu algorytmu GZip przed zapisaniem informacje w bazie danych trwałości. Dozwolone wartości dla tej właściwości: GZip i brak. Wartość domyślna to Brak. Poniższa lista zawiera opis tych opcji.  
  
1.  **GZip**. Dostawca trwałości koduje informacje o stanie przy użyciu algorytmu GZip przed wprowadzeniem trwałych informacje o stanie w bazie danych trwałości.  
  
2.  **Brak**. Dostawca trwałości nie przeprowadza kodowania informacje o stanie przed zapisaniem informacji do bazy danych trwałości.  
  
 Kodowanie informacji stanu wystąpienia przepływu pracy za pomocą GZip zmniejsza zużycie pamięci w bazie danych SQL i zmniejsza zużycie sieciowych, jeśli baza danych znajduje się na innym komputerze w sieci z komputera, na którym jest hosta usługi przepływu pracy uruchomiona. Ogólne wskazówki jest skonfigurowanie **opcji kodowanie wystąpienia** właściwości **Brak** Jeśli stanu wystąpienia przepływu pracy jest mała.
