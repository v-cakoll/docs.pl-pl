---
title: '&#39;ReDim&#39; można zmienić tylko wymiar najdalej z prawej strony'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 94e0fe81f7e750a67943b68f2db700e3a7831da1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502589"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39;ReDim&#39; można zmienić tylko wymiar najdalej z prawej strony
A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru. Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy. Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `Preserve` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice w Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Wymiary tablic w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Zachowaj — usuwanie](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
