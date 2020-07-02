---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622146"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue &lt; T &gt; . TryPeek może zwrócić błędną wartość null za pośrednictwem jego parametru out

#### <a name="details"></a>Szczegóły

W niektórych scenariuszach wielowątkowych <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> można zwrócić wartość true, ale wypełnić parametr out wartością null (zamiast poprawnej wartości z możliwością wglądu).

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4.5.1. Uaktualnienie do tego środowiska spowoduje rozwiązanie tego problemu.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
