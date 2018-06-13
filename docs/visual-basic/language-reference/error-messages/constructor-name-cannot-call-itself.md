---
title: Konstruktor &#39; &lt;nazwa&gt; &#39; nie może wywołać się
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 069de813a0426230e19cddf14c3b83d40a602a41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588999"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Konstruktor &#39; &lt;nazwa&gt; &#39; nie może wywołać się
A `Sub New` procedury w klasie lub strukturze wywołuje sam siebie.  
  
 Konstruktor ma na celu zainicjować wystąpienia klasy lub struktury przy pierwszym. Klasy lub struktury może mieć kilka konstruktorów, pod warunkiem wszystkie mają listy różnych parametrów. Konstruktor służyć do wywoływania innego konstruktora do wykonania jego funkcje oprócz własnego. Ale go nie ma znaczenia dla konstruktora wywołać się, a w rzeczywistości skutkowałoby to nieskończoną rekursję Jeśli dozwolone.  
  
 **Identyfikator błędu:** BC30298  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zapoznaj się z listą parametrów wywoływana z konstruktora. Należy go innym niż wywołania konstruktora.  
  
2.  Jeśli nie zamierzasz wywołać innego konstruktora, Usuń `Sub New` wywołać całkowicie.  
  
## <a name="see-also"></a>Zobacz też  
 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
