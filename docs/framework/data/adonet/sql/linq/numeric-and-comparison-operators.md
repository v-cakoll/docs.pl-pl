---
title: Operatory numeryczne i porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781293"
---
# <a name="numeric-and-comparison-operators"></a>Operatory numeryczne i porównania

Operatory arytmetyczne i porównania działają zgodnie z oczekiwaniami w środowisku uruchomieniowym języka wspólnego (CLR), z wyjątkiem następujących:

- SQL nie obsługuje operatora modulo w liczbie zmiennoprzecinkowej.

- SQL nie obsługuje niesprawdzonej arytmetycznej.

- Operatory zwiększania i zmniejszania powodują skutki uboczne, gdy są używane w wyrażeniach, które nie mogą być replikowane w języku SQL, dlatego nie są obsługiwane.

## <a name="supported-operators"></a>Obsługiwane operatory

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje następujące operatory.

- Operatory arytmetyczne w warstwie Podstawowa:

  - `+`

  - `-`odejmowania

  - `*`

  - `/`

  - Visual Basic dzielenia liczb całkowitych (`\`)

  - `%`(Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-`(Negacja Jednoargumentowa)

- Podstawowe operatory porównania:

  - Visual Basic `=` i C#`==`

  - Visual Basic `<>` i C#`!=`

  - Visual Basic`Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](data-types-and-functions.md)
- [Operatory języka C#](../../../../../csharp/language-reference/operators/index.md)
- [Operatory](../../../../../visual-basic/language-reference/operators/index.md)
