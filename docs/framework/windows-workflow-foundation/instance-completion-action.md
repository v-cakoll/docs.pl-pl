---
title: Działanie ukończenia wystąpienia
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044340"
---
# <a name="instance-completion-action"></a>Działanie ukończenia wystąpienia

Właściwość **Akcja ukończenia wystąpienia** usługi SQL Workflow Store umożliwia określenie, czy dane i metadane wystąpień przepływów pracy są usuwane z bazy danych trwałości po zakończeniu wystąpień. Dozwolone wartości tej właściwości to **DeleteAll** i **DeleteNothing**. Poniższa lista zawiera opis tych opcji:

- **DeleteAll (domyślnie).** Jeśli wartość właściwości jest ustawiona na DeleteAll, dane i metadane wystąpień przepływów pracy są usuwane z bazy danych trwałości po zakończeniu wystąpień.

- **DeleteNothing.** Jeśli wartość właściwości jest ustawiona na DeleteNothing, dane i metadane wystąpień przepływu pracy są przechowywane w bazie danych trwałości nawet po zakończeniu wystąpień.

  > [!CAUTION]
  > Zachowywanie informacji o stanie wystąpienia po zakończeniu wystąpień powoduje, że baza danych trwałości zostanie powiększona. Ponieważ rozmiar bazy danych powiększa operacje bazy danych wykonywane przez podsystem trwałości, w związku z czym konieczne będzie przeczyszczenie informacji o stanie wystąpienia z bazy danych trwałości okresowo, aby usługi były wykonywane na poziomie, który spełnia Twoje wymagania wymagania dotyczące wydajności.
