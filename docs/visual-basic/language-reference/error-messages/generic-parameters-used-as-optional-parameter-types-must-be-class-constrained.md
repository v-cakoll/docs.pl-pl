---
title: "Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords: BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a13ea66f12e54db4e585577e20e1f5396669f1a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Parametry ogólne używane jako typy parametrów opcjonalnych muszą być ograniczone przez klasę
Procedura jest zadeklarowana z opcjonalnym parametrem, który używa parametru typu, który nie jest ograniczona do typu referencyjnego.  
  
 Należy zawsze podać wartość domyślną dla każdego parametru opcjonalnego. Jeśli parametr jest typu referencyjnego, opcjonalna wartość musi być `Nothing`, która jest prawidłową wartością dla dowolnego typu odwołania. Jednak jeśli parametr jest typu wartości, typu musi być typem danych podstawowych wstępnie zdefiniowane przez program Visual Basic. Jest to spowodowane typu złożonego wartość, na przykład struktury zdefiniowane przez użytkownika, nie ma prawidłowe wartości domyślnej.  
  
 Gdy używasz parametru typu dla parametru opcjonalnego musi zagwarantowania, że będzie typu odwołania, aby uniknąć możliwości bez wartości prawidłowy domyślny typ wartości. Oznacza to, że parametr typu należy ograniczyć za pomocą `Class` — słowo kluczowe lub o nazwie określonej klasy.  
  
 **Identyfikator błędu:** BC32124  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ograniczenie parametru typu do akceptowania tylko typem referencyjnym lub nie jest używana dla parametru opcjonalnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
