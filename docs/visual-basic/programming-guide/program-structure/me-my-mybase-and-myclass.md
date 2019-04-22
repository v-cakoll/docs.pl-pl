---
title: Me, My, MyBase i MyClass w Visual Basic
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a8df6e48fd5bce9bb28d8aef7e031f36741ad0ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813395"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase i MyClass w Visual Basic
`Me`, `My`, `MyBase` i `MyClass` w języku Visual Basic mają podobne nazwy, ale różne cele. W tym temacie opisano każdy z tych obiektów w celu ich rozróżnienia.  
  
## <a name="me"></a>Me  
 Słowo kluczowe `Me` umożliwia odwołanie się do konkretnego wystąpienia klasy lub struktury, w którym aktualnie wykonywany jest kod. `Me` zachowuje się jak zmienna obiektu lub struktury, odwołując się do bieżącego wystąpienia. Używanie słowa kluczowego `Me` jest szczególnie przydatne do przekazywania informacji o aktualnie wykonywanej instancji klasy lub struktury do procedury w innej klasie, strukturze lub module.  
  
 Załóżmy na przykład, że masz w module następującą procedurę.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Możesz wywołać tę procedurę i przekazać bieżące wystąpienie klasy <xref:System.Windows.Forms.Form> jako argument, używając następującej instrukcji.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 Właściwość `My` pozwala na łatwy i intuicyjny dostęp do wielu klas [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], umożliwiając użytkownikowi języka Visual Basic interakcję z komputerem, aplikacją, ustawieniami, zasobami i innymi elementami.  
  
## <a name="mybase"></a>MyBase  
 Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy bazowej bieżącego wystąpienia klasy. Słowo kluczowe `MyBase` jest najczęściej używane do dostępu do składowych klasy bazowej, które zostały zastąpione lub przesłonięte w klasie pochodnej. `MyBase.New` służy do jawnego wywołania konstruktora klasy bazowej w konstruktorze klasy pochodnej.  
  
## <a name="myclass"></a>MyClass  
 Słowo kluczowe `MyClass` zachowuje się jak odwołanie do bieżącego wystąpienia klasy zgodnie z pierwotną implementacją. `MyClass` przypomina `Me`, ale wszystkie wywołania metod na tym słowie kluczowym są traktowane tak, jakby były `NotOverridable`.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
