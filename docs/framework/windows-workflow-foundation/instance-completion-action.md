---
title: Działanie ukończenia wystąpienia
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: d68f41a586e44f96c9ca26cf8a142a2782adaa36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662978"
---
# <a name="instance-completion-action"></a>Działanie ukończenia wystąpienia
**Działanie ukończenia wystąpienia** właściwość Store wystąpienia przepływu pracy SQL pozwala określić, czy dane i metadane wystąpienia przepływu pracy jest usuwane z bazy danych trwałości po ukończeniu wystąpienia. Dozwolone wartości dla tej właściwości to **DeleteAll** i **DeleteNothing**. Na poniższej liście opisano te opcje:  
  
- **DeleteAll (ustawienie domyślne).** Jeśli wartość właściwości jest równa DeleteAll, danych i metadanych wystąpienia przepływu pracy został usunięty z bazy danych trwałości po ukończeniu wystąpienia.  
  
- **DeleteNothing.** Jeśli wartość właściwości jest równa DeleteNothing, danych i metadanych wystąpienia przepływu pracy jest przechowywana w bazie danych trwałości mimo wystąpienia są wykonywane.  
  
    > [!CAUTION]
    >  Przechowywanie informacji o stanie wystąpienie po ukończone przyczyny wystąpienia bazy danych trwałości zwiększanie się rozmiaru. Wzrostem rozmiaru bazy danych operacji bazy danych, wykonywanych przez podsystem trwałości trwać dłużej, warto je Wyczyść informacje o stanie wystąpienie z bazy danych trwałości okresowo, aby ma wykonywać na poziomie usług integracji, które spełniają Twoje wymagań dotyczących wydajności.
