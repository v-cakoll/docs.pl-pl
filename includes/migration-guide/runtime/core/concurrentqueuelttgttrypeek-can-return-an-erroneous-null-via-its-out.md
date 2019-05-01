---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664326"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue\<T >. TryPeek może zwrócić poproszenie o wartości null za pośrednictwem jego parametru ze specyfikatorem out

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach wielowątkowych <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> może zwrócić wartość true, ale wypełnić parametr out o wartości null (a nie wartość poprawny, podejrzeć).|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.5.1. Uaktualnienie do tej struktury rozwiąże problem.|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
