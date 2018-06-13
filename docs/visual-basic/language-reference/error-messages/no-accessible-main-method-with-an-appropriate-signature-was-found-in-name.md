---
title: Brak dostępnego &#39;Main&#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwy&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593223"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Brak dostępnego &#39;Main&#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwy&gt;&#39;
Aplikacje wiersza poleceń musi mieć `Sub Main` zdefiniowane. `Main` musi być zadeklarowany jako `Public Shared` , jeśli jest on zdefiniowany w klasie lub jako `Public` Jeśli zdefiniowany w module.  
  
 **Identyfikator błędu:** BC30737  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdefiniuj `Public Sub Main` procedury dla projektu. Zadeklaruj ją jako `Shared` tylko wtedy, gdy należy zdefiniować wewnątrz klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
