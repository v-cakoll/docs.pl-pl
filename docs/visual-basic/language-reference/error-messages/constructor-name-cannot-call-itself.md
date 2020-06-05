---
title: Konstruktor „<name>” nie może wywołać sam siebie
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409806"
---
# <a name="constructor-name-cannot-call-itself"></a>Konstruktor „\<name>” nie może wywołać sam siebie
`Sub New`Procedura w klasie lub strukturze wywołuje sam siebie.  
  
 Celem konstruktora jest zainicjowanie wystąpienia klasy lub struktury, gdy jest ona najpierw tworzona. Klasa lub struktura może mieć kilka konstruktorów, pod warunkiem, że wszystkie mają różne listy parametrów. Konstruktor jest uprawniony do wywołania innego konstruktora, aby wykonywał jego funkcję oprócz własnych. Jednak nie ma to znaczenia dla konstruktora, który wywołuje siebie, i w rzeczywistości spowoduje nieskończoną rekursję, jeśli jest to dozwolone.  
  
 **Identyfikator błędu:** BC30298  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź listę parametrów wywoływanego konstruktora. Powinien być różny od konstruktora wywołującego wywołanie.  
  
2. Jeśli nie zamierzasz wywołać innego konstruktora, Usuń `Sub New` wywołanie całkowicie.  
  
## <a name="see-also"></a>Zobacz też

- [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
