---
title: Działanie ukończenia wystąpienia
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791121"
---
# <a name="instance-completion-action"></a>Działanie ukończenia wystąpienia
**Działanie ukończenia wystąpienia** właściwość Store wystąpienia przepływu pracy SQL pozwala określić, czy dane i metadane wystąpienia przepływu pracy jest usuwane z bazy danych trwałości po ukończeniu wystąpienia. Dozwolone wartości dla tej właściwości to **DeleteAll** i **DeleteNothing**. Na poniższej liście opisano te opcje:  
  
- **DeleteAll (ustawienie domyślne).** Jeśli wartość właściwości jest równa DeleteAll, danych i metadanych wystąpienia przepływu pracy został usunięty z bazy danych trwałości po ukończeniu wystąpienia.  
  
- **DeleteNothing.** Jeśli wartość właściwości jest równa DeleteNothing, danych i metadanych wystąpienia przepływu pracy jest przechowywana w bazie danych trwałości mimo wystąpienia są wykonywane.  
  
    > [!CAUTION]
    >  Przechowywanie informacji o stanie wystąpienie po ukończone przyczyny wystąpienia bazy danych trwałości zwiększanie się rozmiaru. Wzrostem rozmiaru bazy danych operacji bazy danych, wykonywanych przez podsystem trwałości trwać dłużej, warto je Wyczyść informacje o stanie wystąpienie z bazy danych trwałości okresowo, aby ma wykonywać na poziomie usług integracji, które spełniają Twoje wymagań dotyczących wydajności.
