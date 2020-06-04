---
title: Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 273ea592e73be5d76a4ffef077e691014a108347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402930"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę
Procedura jest zadeklarowana z opcjonalnym parametrem, który używa parametru typu, który nie jest ograniczony do typu referencyjnego.  
  
 Należy zawsze podać wartość domyślną dla każdego opcjonalnego parametru. Jeśli parametr jest typu referencyjnego, wartość opcjonalna musi być `Nothing` , która jest prawidłową wartością dla dowolnego typu odwołania. Jeśli jednak parametr ma typ wartości, ten typ musi być typem danych podstawowych wstępnie zdefiniowanym przez Visual Basic. Wynika to z faktu, że złożony typ wartości, taki jak struktura zdefiniowana przez użytkownika, nie ma prawidłowej wartości domyślnej.  
  
 W przypadku użycia parametru typu dla parametru opcjonalnego należy zagwarantować, że jest typem referencyjnym, aby uniknąć możliwości typu wartości bez prawidłowej wartości domyślnej. Oznacza to, że należy ograniczyć parametr typu za pomocą `Class` słowa kluczowego lub nazwy konkretnej klasy.  
  
 **Identyfikator błędu:** BC32124  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ogranicz parametr typu, aby akceptował tylko typ referencyjny, lub nie używaj go dla parametru opcjonalnego.  
  
## <a name="see-also"></a>Zobacz też

- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../statements/type-list.md)
- [Class, instrukcja](../statements/class-statement.md)
- [Parametry opcjonalne](../../programming-guide/language-features/procedures/optional-parameters.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Nothing](../nothing.md)
