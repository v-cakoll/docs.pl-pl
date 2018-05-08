---
title: Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 7494f7d6a3897d56419f9d3aa96668fd9dab5f35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)
Jeśli [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy zawierające element członkowski o tej samej sygnaturze, a następnie wykonania ten element członkowski klasy spowoduje, że oba interfejsy do użycia tego elementu członkowskiego jako ich wdrażania. W poniższym przykładzie wszystkie wywołania do `Paint` wywołanie tej samej metody.  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 Jeśli dwa [interfejsu](../../../csharp/language-reference/keywords/interface.md) elementów członkowskich nie wykonuj tę samą funkcję, jednak może to prowadzić do niepoprawna implementacja jednej lub obu interfejsów. Istnieje możliwość jawnie implementować elementu członkowskiego interfejsu — Tworzenie elementu członkowskiego klasy, która jest wywoływana tylko za pośrednictwem interfejsu i specyficzne dla interfejsu. Odbywa się za pomocą nazw elementu członkowskiego klasy o nazwie interfejs i okres. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 Element członkowski klasy `IControl.Paint` są dostępne tylko w `IControl` interfejsu i `ISurface.Paint` są dostępne tylko w `ISurface`. Zarówno implementacje metod są oddzielone i nie będzie dostępny bezpośrednio w klasie. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 Jawna implementacja jest również używany do rozpoznawania przypadków, gdy dwa interfejsy zadeklarować inne elementy członkowskie o tej samej nazwie, takie jak właściwości i metody:  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Aby zaimplementować dotyczą obu interfejsów, klasa ma Użyj jawnej implementacji dla właściwości P lub metody P i/lub aby uniknąć błędów kompilatora. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
