---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615726"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Sprawdzanie poprawności schematu XSD teraz prawidłowo wykrywa naruszenia unikatowych ograniczeń, jeśli są używane klucze złożone, a jeden klucz jest pusty.

#### <a name="details"></a>Szczegóły

Wersje .NET Framework wcześniejsze niż 4,6 miały usterkę, która spowodowała, że Walidacja XSD nie wykryła unikatowych ograniczeń dla kluczy złożonych, jeśli jeden z kluczy był pusty. W .NET Framework 4,6 ten problem został rozwiązany. Spowoduje to dokładniejsze sprawdzenie poprawności, ale może także spowodować, że niektóre XML nie będą sprawdzać, które wcześniej byłyby.

#### <a name="suggestion"></a>Sugestia

W przypadku konieczności walidacji .NET Framework 4,0, sprawdzanie poprawności aplikacji może wskazywać na wersję 4,5 (lub wcześniejszą) .NET Framework. Po przekierowaniu do .NET Framework 4,6, należy jednak przeprowadzić przegląd kodu, aby upewnić się, że nie można zweryfikować zduplikowanych kluczy złożonych (zgodnie z opisem w opisie tego problemu).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6         |
| Typ    | Przekierowanie |
