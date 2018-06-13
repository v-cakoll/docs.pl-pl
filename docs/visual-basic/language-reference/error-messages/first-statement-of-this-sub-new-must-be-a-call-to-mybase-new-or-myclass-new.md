---
title: Pierwsza instrukcja tego &#39;Sub New&#39; musi być wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; (nr dostępny żaden konstruktor bez parametrów)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589463"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>Pierwsza instrukcja tego &#39;Sub New&#39; musi być wywołaniem &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; (nr dostępny żaden konstruktor bez parametrów)
Pierwsza instrukcja tego elementu "Sub New" musi być wywołanie "MyBase.New" lub "MyClass.New", ponieważ klasa podstawowa\<nazwę bazową > "z"\<derivedname > "nie ma dostępnego elementu"Sub New", który można wywołać bez argumentów.  
  
 W klasie pochodnej, co konstruktor musi wywoływać konstruktora klasy podstawowej (`MyBase.New`). Jeśli klasa podstawowa ma konstruktora bez parametrów, który jest dostępny dla klas pochodnych `MyBase.New` wywoływana automatycznie. Jeśli nie, konstruktora klasy podstawowej musi zostać wywołana z parametrami, a nie jest to możliwe automatycznie. W takim przypadku pierwsza instrukcja każdej konstruktora klasy pochodnej musi wywołać sparametryzowane konstruktora dla klasy podstawowej, lub zadzwoń innego konstruktora w klasie pochodnej, która sprawia, że wywołanie konstruktora klasy podstawowej.  
  
 **Identyfikator błędu:** BC30148  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Albo wywołanie `MyBase.New` dostarczanie wymagane parametry lub wywołać konstruktora elementu równorzędnego, który nawiązuje takie połączenie.  
  
     Na przykład, jeśli klasa podstawowa ma konstruktora, który jest zadeklarowany jako `Public Sub New(ByVal index as Integer)`, pierwsza instrukcja w pochodnej konstruktora klasy może być `MyBase.New(100)`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
