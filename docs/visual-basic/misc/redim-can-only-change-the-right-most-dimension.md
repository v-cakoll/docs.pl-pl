---
title: "&#39; ReDim &#39; można zmienić tylko wymiar z prawej"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39; ReDim &#39; można zmienić tylko wymiar z prawej
A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatni wymiar. Korzystając z `Preserve`, zmianie rozmiaru tylko ostatniego wymiaru tablicy. Dla wszystkich innych wymiarów należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `Preserve` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice w Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Wymiary tablicy w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim, instrukcja](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim, instrukcja](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Zachowaj — usuwanie](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
