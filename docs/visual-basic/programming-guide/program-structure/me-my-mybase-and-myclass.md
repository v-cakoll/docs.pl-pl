---
title: Me, My, MyBase i MyClass
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
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347336"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase, i MyClass w Visual Basic
`Me`, `My`, `MyBase`i `MyClass` w Visual Basic mają podobne nazwy, ale inne cele. W tym temacie opisano każdy z tych obiektów w celu ich rozróżnienia.  
  
## <a name="me"></a>Mnie  
 Słowo kluczowe `Me` zapewnia sposób odwoływania się do określonego wystąpienia klasy lub struktury, w której kod jest aktualnie wykonywany. `Me` zachowuje się jak zmienna obiektu lub zmienna struktury odwołująca się do bieżącego wystąpienia. Używanie `Me` jest szczególnie przydatne do przekazywania informacji o aktualnie wykonywanym wystąpieniu klasy lub struktury do procedury w innej klasie, strukturze lub module.  
  
 Załóżmy na przykład, że masz w module następującą procedurę.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Można wywołać tę procedurę i przekazać bieżące wystąpienie klasy <xref:System.Windows.Forms.Form> jako argument przy użyciu następującej instrukcji.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 Funkcja `My` zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, umożliwiając Visual Basic użytkownikowi korzystanie z komputera, aplikacji, ustawień, zasobów i tak dalej.  
  
## <a name="mybase"></a>MyBase  
 Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy podstawowej bieżącego wystąpienia klasy. `MyBase` jest często używany do uzyskiwania dostępu do składowych klasy bazowej, które są zastępowane lub zasłonięte w klasie pochodnej. `MyBase.New` jest używany do jawnego wywoływania konstruktora klasy bazowej z konstruktora klasy pochodnej.  
  
## <a name="myclass"></a>MyClass  
 Słowo kluczowe `MyClass` zachowuje się jak zmienna obiektu odwołująca się do bieżącego wystąpienia klasy jako pierwotnie zaimplementowane. `MyClass` jest podobna do `Me`, ale wszystkie wywołania metod są traktowane jak w przypadku, gdy metoda została `NotOverridable`.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
