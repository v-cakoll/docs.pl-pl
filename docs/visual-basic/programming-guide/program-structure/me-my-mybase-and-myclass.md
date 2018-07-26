---
title: Me, My, MyBase, i MyClass w Visual Basic
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
ms.openlocfilehash: f3db5f8f6688e68992f683ac1b1465078aa41231
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244715"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase, i MyClass w Visual Basic
`Me`, `My`, `MyBase`, i `MyClass` w języku Visual Basic mają podobne nazwy, ale różnych celów. W tym temacie opisano każdy z tych obiektów, aby odróżnić je.  
  
## <a name="me"></a>Mnie  
 `Me` — Słowo kluczowe zapewnia sposób odwołania do konkretnego wystąpienia klasy lub struktury, w którym aktualnie wykonuje kod. `Me` zachowuje się jak zmienna obiektu lub zmiennej struktury, odwołanie do bieżącego wystąpienia. Za pomocą `Me` jest szczególnie przydatne do przekazywania informacji o obecnie wykonywanym wystąpienia klasy lub struktury do procedury w innej klasy, struktury lub modułu.  
  
 Na przykład załóżmy, że masz następujące procedury w module.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Możesz wywołać tę procedurę i przekazywać bieżące wystąpienie <xref:System.Windows.Forms.Form> klasy jako argument przy użyciu następujących instrukcji.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 `My` Funkcji umożliwia łatwe i intuicyjne dostęp do wielu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klas, umożliwiając użytkownikowi języka Visual Basic do interakcji z komputera, aplikacji, ustawień, zasobów i tak dalej.  
  
## <a name="mybase"></a>MyBase  
 `MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu odwołujące się do klasy bazowej bieżącego wystąpienia klasy. `MyBase` jest najczęściej używany do dostępu do składowych klasy bazowej, które zostały zastąpione lub pada w klasie pochodnej. `MyBase.New` Służy do jawnie wywołać konstruktora klasy bazowej w konstruktorze klasy pochodnej.  
  
## <a name="myclass"></a>MyClass  
 `MyClass` — Słowo kluczowe zachowuje się jak odwołanie do bieżącego wystąpienia klasy pierwotnie zaimplementowanych zmiennej obiektu. `MyClass` jest podobny do `Me`, ale wszystkie wywołania metody na nim są traktowane tak, jakby były metody `NotOverridable`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
