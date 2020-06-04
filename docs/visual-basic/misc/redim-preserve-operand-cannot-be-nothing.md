---
title: Argument operacji zachowywania "ReDim" nie może mieć wartości Nothing
ms.date: 07/20/2015
ms.assetid: b857f313-3fc2-4262-a577-88df1718b811
ms.openlocfilehash: 7dc57d328f04b8210adec3cb2bf2c2e29af66313
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358105"
---
# <a name="redim-preserve-operand-cannot-be-nothing"></a>Argument operacji zachowywania "ReDim" nie może mieć wartości Nothing
`ReDim`Instrukcja próbuje użyć `Preserve` słowa kluczowego, aby zmienić wymiar tablicy, która nie jest ostatnim wymiarem, ale nie dostarcza prawidłowej wartości dla tego operandu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień `Preserve` operand na prawidłową wartość.  
  
## <a name="see-also"></a>Zobacz też

- [Tablice w Visual Basic](../programming-guide/language-features/arrays/index.md)
- [Wymiary tablicy w Visual Basic](../programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim, instrukcja](../language-reference/statements/redim-statement.md)
- [Dim, instrukcja](../language-reference/statements/dim-statement.md)
