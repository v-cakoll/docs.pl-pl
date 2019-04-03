---
title: Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1024cf6f2c1fa112db29cb710eef190a5022d3af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838602"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Nie można wywnioskować argumentów typu na podstawie obiektu delegowanego
Używa instrukcji przypisania `AddressOf` na przypisanie adresu ogólnej procedury, aby obiekt delegowany, ale nie dostarcza żadnych argumentów typu rodzajowego procedury.  
  
 Zwykle po wywołaniu typu ogólnego, podaj argument typu dla każdego parametru typu, który definiuje typ ogólny. Jeśli nie podasz żadnych argumentów typu, kompilator spróbuje wnioskowanie typów, które mają być przekazane do parametrów typu. Jeśli kontekst nie zawiera wystarczających informacji, aby kompilator mógł wnioskowanie typów, zostanie wygenerowany błąd.  
  
 **Identyfikator błędu:** BC36564  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Określ argumenty tupu ogólnego procedury w `AddressOf` wyrażenia.  
  
## <a name="see-also"></a>Zobacz także

- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Procedury ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
