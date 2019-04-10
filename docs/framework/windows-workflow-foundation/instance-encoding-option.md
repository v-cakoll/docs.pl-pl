---
title: Opcja kodowania wystąpienia
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315624"
---
# <a name="instance-encoding-option"></a>Opcja kodowania wystąpienia
**Opcja kodowania wystąpienia** właściwość Store wystąpienia przepływu pracy SQL pozwala określić, czy dostawcy stanów trwałych programu SQL należy skompresować informacji stanu wystąpienia przepływu pracy za pomocą algorytmu GZip przed zapisaniem informacje w bazie danych trwałości. Dozwolone wartości dla tej właściwości to: GZip i None. Wartość domyślna to Brak. Na poniższej liście opisano te opcje.  
  
1. **GZip**. Dostawcy stanów trwałych koduje informacje o stanie za pomocą algorytmu GZip przed wprowadzeniem trwałych informacje o stanie w bazie danych trwałości.  
  
2. **Brak**. Dostawcy stanów trwałych nie przeprowadza kodowania informacje o stanie przed zapisaniem informacje do bazy danych trwałości.  
  
 Informacje o stanie wystąpienie przepływu pracy przy użyciu GZip kodowanie zmniejsza zużycie pamięci w bazie danych SQL i zmniejsza użycie sieci, jeśli baza danych znajduje się na innym komputerze w sieci z komputera, na którym jest hosta usługi przepływu pracy uruchomione. Ogólne wskazówki dotyczące polega na ustawieniu **opcja kodowania wystąpienia** właściwości **Brak** Jeśli stan wystąpienia przepływu pracy jest mała.
