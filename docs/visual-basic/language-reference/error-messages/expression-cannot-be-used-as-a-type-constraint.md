---
title: "&#39; &lt;wyrażenia&gt;&#39; nie można użyć jako ograniczenia typu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords: BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 054c05747491afb02601df00225a703560cbe91c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39; &lt;wyrażenia&gt;&#39; nie można użyć jako ograniczenia typu
Lista ograniczeń zawiera wyrażenie, które nie stanowi prawidłowe ograniczenie parametru typu.  
  
 Lista ograniczeń nakłada wymagań dotyczących typu argumentu przekazanego do parametru typu. W dowolnej kombinacji można określić następujące wymagania:  
  
-   Argument typu musi implementować jeden lub więcej interfejsów  
  
-   Argument typu musi dziedziczyć po co najwyżej jedną klasę  
  
-   Argument typu musi ujawniać konstruktor bez parametrów, dostępnym dla tworzenia kodu (obejmują `New` ograniczenia)  
  
 Jeśli na liście ograniczeń nie zostanie uwzględniony określonej klasy lub interfejsu, można skonfigurować więcej ogólnych wymagań, określając jedną z następujących czynności:  
  
-   Argument typu musi być typem wartości (obejmują `Structure` ograniczenia)  
  
-   Argument typu musi być typu odwołania (obejmują `Class` ograniczenia)  
  
 Nie można określić zarówno `Structure` i `Class` dla tego samego typu parametru, a nie można określić jedną więcej niż raz.  
  
 **Identyfikator błędu:** BC32061  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wyrażenie i jej elementy są poprawne.  
  
-   Jeśli wyrażenie nie kwalifikuje się do poprzedniego listę wymagań, należy go usunąć z listy ograniczeń.  
  
-   Wyrażenie odwołuje się do interfejsu lub klasa, sprawdź, czy kompilator ma dostęp do tego interfejsu lub klasy. Może być konieczne jego nazwy, a czasami trzeba dodać odwołanie do projektu. Aby uzyskać więcej informacji, zobacz "Odwołań do projektów" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy wartości i typy referencyjne](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB porady: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
