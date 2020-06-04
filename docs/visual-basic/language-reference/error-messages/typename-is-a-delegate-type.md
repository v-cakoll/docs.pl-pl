---
title: Typ „<typename>” jest typem delegowanym
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 7056bbf2b4de26feba3bfbe0e02b3239311271c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382175"
---
# <a name="typename-is-a-delegate-type"></a>Typ „\<typename>” jest typem delegowanym
\<typename>Typ "" jest typem delegowanym. Konstrukcja delegata zezwala tylko na pojedyncze wyrażenie AddressOf jako listę argumentów. Często wyrażenie AddressOf może być używane zamiast konstrukcji delegata.  
  
 `New`Klauzula tworząca wystąpienie klasy delegata dostarcza do konstruktora delegata nieprawidłową listę argumentów.  
  
 `AddressOf`Podczas tworzenia nowego wystąpienia delegata można podać tylko jedno wyrażenie.  
  
 Ten błąd może wystąpić, jeśli nie przekażesz żadnych argumentów do konstruktora delegata, Jeśli przekażesz więcej niż jeden argument lub przekażesz pojedynczy argument, który nie jest prawidłowym `AddressOf` wyrażeniem.  
  
 **Identyfikator błędu:** BC32008  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj jednego `AddressOf` wyrażenia na liście argumentów dla klasy delegata w `New` klauzuli.  
  
## <a name="see-also"></a>Zobacz też

- [Operator new](../operators/new-operator.md)
- [AddressOf, operator](../operators/addressof-operator.md)
- [Delegaci](../../programming-guide/language-features/delegates/index.md)
- [Instrukcje: wywoływanie metody delegata](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
