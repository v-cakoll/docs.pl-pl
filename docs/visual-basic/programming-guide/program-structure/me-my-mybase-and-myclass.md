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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400849"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase, i MyClass w Visual Basic
`Me`, `My` `MyBase`, `MyClass` i visual basic mają podobne nazwy, ale różne cele. W tym temacie opisano każdą z tych jednostek w celu ich odróżnienia.  
  
## <a name="me"></a>Ja  
 Słowo `Me` kluczowe umożliwia odwoływanie się do określonego wystąpienia klasy lub struktury, w której kod jest obecnie wykonywany. `Me`zachowuje się jak zmienna obiektu lub zmienna struktury odnosząca się do bieżącego wystąpienia. Używanie `Me` jest szczególnie przydatne do przekazywania informacji o aktualnie wykonywanym wystąpieniu klasy lub struktury do procedury w innej klasie, strukturze lub module.  
  
 Załóżmy na przykład, że w module jest niżej niżej sześc.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Można wywołać tę procedurę i przekazać <xref:System.Windows.Forms.Form> bieżące wystąpienie klasy jako argument przy użyciu następującej instrukcji.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 Funkcja `My` ta zapewnia łatwy i intuicyjny dostęp do wielu klas programu .NET Framework, umożliwiając użytkownikowi języka Visual Basic interakcję z komputerem, aplikacją, ustawieniami, zasobami i tak dalej.  
  
## <a name="mybase"></a>Mybase  
 Słowo `MyBase` kluczowe zachowuje się jak zmienna obiektowa odnosząca się do klasy podstawowej bieżącego wystąpienia klasy. `MyBase`jest powszechnie używany do uzyskiwania dostępu do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowane w klasie pochodnej. `MyBase.New`jest używany do jawnego wywołania konstruktora klasy podstawowej z konstruktora klas pochodnych.  
  
## <a name="myclass"></a>Myclass  
 Słowo `MyClass` kluczowe zachowuje się jak zmienna obiektowa odnosząca się do bieżącego wystąpienia klasy, jak pierwotnie zaimplementowano. `MyClass`jest podobny `Me`do , ale wszystkie wywołania metody na `NotOverridable`to są traktowane tak, jakby metoda była .  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
