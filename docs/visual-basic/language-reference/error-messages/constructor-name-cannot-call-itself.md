---
title: Konstruktor &#39; &lt;nazwa&gt; &#39; nie może wywołać sam siebie
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 4a02277893147716098a3dcc327e221e0775d476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662728"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Konstruktor &#39; &lt;nazwa&gt; &#39; nie może wywołać sam siebie
A `Sub New` procedury w klasie lub strukturze wywołuje sam siebie.  
  
 Konstruktor ma na celu zainicjować wystąpienia klasy lub struktury, gdy po raz pierwszy. Klasa lub struktura może mieć kilka konstruktorów, pod warunkiem, wszystkie one mają listy różnych parametrów. Konstruktor jest dozwolony do wywoływania innego konstruktora, przeprowadzić jego funkcje oprócz swój własny. Ale jest całkowicie nieprzydatna dla konstruktora wywołać sam siebie, a w rzeczywistości spowoduje to nieskończoną rekursję Jeśli dozwolone.  
  
 **Identyfikator błędu:** BC30298  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź listę parametrów konstruktora wywoływanego. Należy go innym niż Konstruktor wykonuje wywołanie.  
  
2.  Jeśli nie zamierzasz wywołanie innego konstruktora, Usuń `Sub New` wywołań w całości.  
  
## <a name="see-also"></a>Zobacz także
- [Okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
