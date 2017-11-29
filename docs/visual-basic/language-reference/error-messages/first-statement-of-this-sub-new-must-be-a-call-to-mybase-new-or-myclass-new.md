---
title: "Pierwsza instrukcja tego &#39; Sub nowy &#39; musi być wywołanie &#39; MyBase.New &#39; i &#39; MyClass.New &#39; (Brak dostępnych konstruktora bez parametrów)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords: BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>Pierwsza instrukcja tego &#39; Sub nowy &#39; musi być wywołanie &#39; MyBase.New &#39; i &#39; MyClass.New &#39; (Brak dostępnych konstruktora bez parametrów)
Pierwsza instrukcja tego elementu "Sub New" musi być wywołanie "MyBase.New" lub "MyClass.New", ponieważ klasa podstawowa\<nazwę bazową > "z"\<derivedname > "nie ma dostępnego elementu"Sub New", który można wywołać bez argumentów.  
  
 W klasie pochodnej, co konstruktor musi wywoływać konstruktora klasy podstawowej (`MyBase.New`). Jeśli klasa podstawowa ma konstruktora bez parametrów, który jest dostępny dla klas pochodnych `MyBase.New` wywoływana automatycznie. Jeśli nie, konstruktora klasy podstawowej musi zostać wywołana z parametrami, a nie jest to możliwe automatycznie. W takim przypadku pierwsza instrukcja każdej konstruktora klasy pochodnej musi wywołać sparametryzowane konstruktora dla klasy podstawowej, lub zadzwoń innego konstruktora w klasie pochodnej, która sprawia, że wywołanie konstruktora klasy podstawowej.  
  
 **Identyfikator błędu:** BC30148  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Albo wywołanie `MyBase.New` dostarczanie wymagane parametry lub wywołać konstruktora elementu równorzędnego, który nawiązuje takie połączenie.  
  
     Na przykład, jeśli klasa podstawowa ma konstruktora, który jest zadeklarowany jako `Public Sub New(ByVal index as Integer)`, pierwsza instrukcja w pochodnej konstruktora klasy może być `MyBase.New(100)`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
