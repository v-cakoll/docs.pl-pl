---
ms.openlocfilehash: 5844dbc2c3c89baeb39b69f16846f92ac10e97f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804587"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Sprawdzanie poprawności schematu XSD teraz poprawnie wykrywa naruszenia unikatowych ograniczeń, jeśli używane są klucze złożone, a jeden klucz jest pusty

|   |   |
|---|---|
|Szczegóły|Wersje programu .NET Framework przed 4.6 miał błąd, który spowodował sprawdzanie poprawności XSD nie wykryć unikatowe ograniczenia kluczy złożonych, jeśli jeden z kluczy był pusty. W .NET Framework 4.6 ten problem został rozwiązany. Spowoduje to bardziej poprawne sprawdzanie poprawności, ale może również spowodować, że niektóre XML nie sprawdzania poprawności, które wcześniej będzie miało.|
|Sugestia|Jeśli jest to konieczne luźniejsze sprawdzanie poprawności programu .NET Framework 4.0, aplikacja sprawdzania poprawności może kierować na wersję 4.5 (lub wcześniejszą) programu .NET Framework. Podczas retargeting do .NET Framework 4.6, jednak przegląd kodu należy wykonać, aby upewnić się, że zduplikowane klucze złożone (zgodnie z opisem tego problemu) nie powinny sprawdzać poprawności.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Przekierowanie|
