---
title: Operatory numeryczne i porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: ff54856a66ad5e9c0362c013f8df5f1147055cd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915710"
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

- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operatory języka C#](../../../../../csharp/language-reference/operators/index.md)
- [Operatory](../../../../../visual-basic/language-reference/operators/index.md)
