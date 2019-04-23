---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804718"
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
