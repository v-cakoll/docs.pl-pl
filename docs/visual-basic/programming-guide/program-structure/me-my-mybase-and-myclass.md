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
ms.openlocfilehash: 7df146e09a1d7cd730f4cf539d6823f7ced44bd1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002535"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase, i MyClass w Visual Basic
`Me`, `My`, `MyBase` i `MyClass` w Visual Basic mają podobne nazwy, ale w różnych celach. W tym temacie opisano każdą z tych jednostek, aby je rozróżnić.  
  
## <a name="me"></a>Mnie  
 Słowo kluczowe `Me` umożliwia odwoływanie się do określonego wystąpienia klasy lub struktury, w której kod jest aktualnie wykonywany. `Me` zachowuje się jak zmienna obiektu lub zmienna struktury odwołująca się do bieżącego wystąpienia. Używanie `Me` jest szczególnie przydatne do przekazywania informacji o aktualnie wykonywanym wystąpieniu klasy lub struktury do procedury w innej klasie, strukturze lub module.  
  
 Załóżmy na przykład, że masz poniższą procedurę w module.  
  
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
 Funkcja `My` zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, umożliwiając Visual Basic użytkownikowi współpracujące z komputerem, aplikacją, ustawieniami, zasobami i tak dalej.  
  
## <a name="mybase"></a>MyBase  
 Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy podstawowej bieżącego wystąpienia klasy. `MyBase` jest często używany do uzyskiwania dostępu do składowych klasy bazowej, które są zastępowane lub zasłonięte w klasie pochodnej. `MyBase.New` służy do jawnego wywołania konstruktora klasy bazowej z konstruktora klasy pochodnej.  
  
## <a name="myclass"></a>MyClass  
 Słowo kluczowe `MyClass` zachowuje się jak zmienna obiektu odwołująca się do bieżącego wystąpienia klasy jako pierwotnie zaimplementowane. `MyClass` jest podobna do `Me`, ale wszystkie wywołania metody są traktowane tak, jakby Metoda była `NotOverridable`.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
