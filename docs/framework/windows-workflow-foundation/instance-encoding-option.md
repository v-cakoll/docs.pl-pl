---
title: Opcja kodowania wystąpienia
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: cfe45428f546b6f47709c321099efdf7fbb25ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512541"
---
# <a name="instance-encoding-option"></a>Opcja kodowania wystąpienia
**Opcji kodowanie wystąpienia** właściwość w magazynie wystąpień przepływu pracy SQL umożliwia określenie, czy dostawca trwałości SQL należy skompresować informacji stanu wystąpienia przepływu pracy przy użyciu algorytmu GZip przed zapisaniem informacje w bazie danych trwałości. Dozwolone wartości dla tej właściwości: GZip i brak. Wartość domyślna to Brak. Poniższa lista zawiera opis tych opcji.  
  
1.  **GZip**. Dostawca trwałości koduje informacje o stanie przy użyciu algorytmu GZip przed wprowadzeniem trwałych informacje o stanie w bazie danych trwałości.  
  
2.  **Brak**. Dostawca trwałości nie przeprowadza kodowania informacje o stanie przed zapisaniem informacji do bazy danych trwałości.  
  
 Kodowanie informacji stanu wystąpienia przepływu pracy za pomocą GZip zmniejsza zużycie pamięci w bazie danych SQL i zmniejsza zużycie sieciowych, jeśli baza danych znajduje się na innym komputerze w sieci z komputera, na którym jest hosta usługi przepływu pracy uruchomiona. Ogólne wskazówki jest skonfigurowanie **opcji kodowanie wystąpienia** właściwości **Brak** Jeśli stanu wystąpienia przepływu pracy jest mała.
