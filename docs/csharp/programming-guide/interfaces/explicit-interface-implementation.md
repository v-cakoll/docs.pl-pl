---
title: Implementacja interfejsu jawnego C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ac90726fd50f104d1b9251d4f9b097b721ea5e7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75701761"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)
Jeśli [Klasa](../../language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski o tym samym podpisie, a następnie wdrożenie tego elementu członkowskiego w klasie spowoduje, że oba interfejsy używają tego elementu członkowskiego jako ich implementacji. W poniższym przykładzie wszystkie wywołania do `Paint` wywołują tę samą metodę.  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 Jeśli dwa elementy członkowskie [interfejsu](../../language-reference/keywords/interface.md) nie wykonują tej samej funkcji, może to jednak prowadzić do niepoprawnej implementacji jednego lub obu interfejsów. Istnieje możliwość jawnej implementacji elementu członkowskiego interfejsu — tworzenie składowej klasy, która jest wywoływana tylko przez interfejs i jest specyficzna dla tego interfejsu. Jest to realizowane przez nazywanie składowej klasy nazwą interfejsu i kropką. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 `IControl.Paint` elementu członkowskiego klasy jest dostępna tylko za pomocą interfejsu `IControl`, a `ISurface.Paint` jest dostępny tylko za pomocą `ISurface`. Obie implementacje metod są oddzielone, a żaden z nich nie jest dostępny bezpośrednio w klasie. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 Jawna implementacja służy również do rozwiązywania przypadków, gdy dwa interfejsy deklarują różne elementy członkowskie o tej samej nazwie, takie jak właściwość i Metoda:  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 Aby zaimplementować oba interfejsy, Klasa musi używać jawnej implementacji dla właściwości P, lub metody P lub obu, aby uniknąć błędu kompilatora. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
