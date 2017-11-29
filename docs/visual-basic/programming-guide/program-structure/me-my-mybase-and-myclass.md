---
title: Me, My, MyBase, i MyClass w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Me, My, MyBase, i MyClass w Visual Basic
`Me`, `My`, `MyBase`, i `MyClass` w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] mają podobne nazwy, ale różnych celów. W tym temacie opisano każdy z tych obiektów, aby odróżnić je.  
  
## <a name="me"></a>Mnie  
 `Me` — Słowo kluczowe zapewnia sposób odwołania do konkretnego wystąpienia klasy lub struktury, w którym kod jest aktualnie wykonywany. `Me`zachowuje się jak zmienna obiektu lub zmienna struktury odwołanie do bieżącego wystąpienia. Przy użyciu `Me` jest szczególnie przydatne podczas przekazywania informacji o obecnie wykonywanym wystąpienia klasy lub struktury do procedury w innej klasy, struktury lub modułu.  
  
 Na przykład załóżmy, że masz następujące procedury w module.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Możesz nazwać tę procedurę i przekazać bieżące wystąpienie klasy <xref:System.Windows.Forms.Form> klasy jako argument przy użyciu następujących instrukcji.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Moje  
 `My` Funkcji umożliwia proste i intuicyjne dostęp do wielu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klas, włączanie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] użytkownika do interakcji z komputera, aplikacji, ustawień, zasobów i tak dalej.  
  
## <a name="mybase"></a>MyBase  
 `MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu odwołujące się do klasy bazowej bieżącego wystąpienia klasy. `MyBase`jest najczęściej używany do dostęp do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowanie w klasie pochodnej. `MyBase.New`Służy do jawnie wywołać konstruktora klasy podstawowej z konstruktora klasy pochodnej.  
  
## <a name="myclass"></a>MyClass  
 `MyClass` — Słowo kluczowe zachowuje się jak zmienna obiektu odwołanie do bieżącego wystąpienia klasy pierwotnie zaimplementowanych. `MyClass`przypomina `Me`, ale wszystkie wywołania metody na nim są traktowane jak gdyby metoda `NotOverridable`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
