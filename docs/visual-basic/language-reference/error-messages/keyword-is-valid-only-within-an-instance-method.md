---
title: '&#39;&lt;słowo kluczowe&gt; &#39; jest prawidłowy tylko wewnątrz metody wystąpienia'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586363"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a>&#39;&lt;słowo kluczowe&gt; &#39; jest prawidłowy tylko wewnątrz metody wystąpienia
`Me`, `MyClass`, I `MyBase` słowa kluczowe odwoływać się do wystąpień określonej klasy. Nie można ich używać w udostępnionej `Function` lub `Sub` procedury.  
  
 **Identyfikator błędu:** BC30043  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń słowo kluczowe z procedury lub usuń `Shared` — słowo kluczowe z deklaracji procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Przypisanie zmiennej obiektu](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
