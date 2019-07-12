---
ms.openlocfilehash: c0a281b05f453b68495e6fa6fca45f3f36a204a3
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804587"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>Weryfikacja schematu XSD teraz prawidłowo wykrywa naruszenia ograniczenia unikatowe klucze złożone są używane, jeśli jeden klucz jest pusty

|   |   |
|---|---|
|Szczegóły|Wersje programu .NET Framework przed 4.6 miał usterkę powodującą walidację XSD nie wykryć ograniczenia unikatowe klucze złożone, jeśli jeden z kluczy był pusty. W .NET Framework 4.6 ten problem został rozwiązany. Spowoduje to bardziej poprawny sprawdzania poprawności, ale także może spowodować pewne XML nie weryfikacji, który wcześniej miałby.|
|Sugestia|W razie potrzeby im weryfikacji programu .NET Framework 4.0 weryfikowania aplikacji można wskazać w wersji 4.5 (lub starszym) programu .NET Framework. W przypadku przekierowania do .NET Framework 4.6, jednak przeglądu kodu powinna być podejmowana należy upewnić się, że zduplikowane klucze złożone (zgodnie z opisem w opisie tego problemu) najprawdopodobniej nie można zweryfikować.|
|Scope|Krawędź|
|Wersja|4.6|
|Typ|Przekierowanie|

