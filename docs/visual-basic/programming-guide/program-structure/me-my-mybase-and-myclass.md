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
ms.openlocfilehash: b4470e5c178c0f66dc33956ea0131d4eabc51d46
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397496"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase, i MyClass w Visual Basic
`Me`, `My` , `MyBase` , i `MyClass` w Visual Basic mają podobne nazwy, ale różne cele. W tym temacie opisano każdą z tych jednostek, aby je rozróżnić.  
  
## <a name="me"></a>Ja  
 `Me`Słowo kluczowe umożliwia odwoływanie się do określonego wystąpienia klasy lub struktury, w której kod jest aktualnie wykonywany. `Me`zachowuje się jak zmienna obiektu lub zmienna struktury odwołująca się do bieżącego wystąpienia. Użycie `Me` jest szczególnie przydatne w przypadku przekazywania informacji o aktualnie wykonywanym wystąpieniu klasy lub struktury do procedury w innej klasie, strukturze lub module.  
  
 Załóżmy na przykład, że masz poniższą procedurę w module.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Można wywołać tę procedurę i przekazać bieżące wystąpienie <xref:System.Windows.Forms.Form> klasy jako argument przy użyciu następującej instrukcji.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 Ta `My` Funkcja zapewnia łatwy i intuicyjny dostęp do kilku klas .NET Framework, umożliwiając Visual Basic użytkownikowi współpracujący z komputerem, aplikacją, ustawieniami, zasobami itd.  
  
## <a name="mybase"></a>MyBase  
 `MyBase`Słowo kluczowe zachowuje się jak zmienna obiektu odwołująca się do klasy podstawowej bieżącego wystąpienia klasy. `MyBase`jest często używany do uzyskiwania dostępu do składowych klasy bazowej, które są zastępowane lub zasłonięte w klasie pochodnej. `MyBase.New`służy do jawnego wywołania konstruktora klasy bazowej z konstruktora klasy pochodnej.  
  
## <a name="myclass"></a>MyClass  
 `MyClass`Słowo kluczowe zachowuje się jak zmienna obiektu odwołująca się do bieżącego wystąpienia klasy jako pierwotnie zaimplementowane. `MyClass`jest podobny do `Me` , ale wszystkie wywołania metody są traktowane jak w przypadku metody `NotOverridable` .  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe informacje o dziedziczeniu](../language-features/objects-and-classes/inheritance-basics.md)
