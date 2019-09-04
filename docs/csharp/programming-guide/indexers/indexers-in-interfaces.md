---
title: Indeksatory w interfejsach C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 7f52df0283cf057c1cd6cc4fa87c0086da7e61d2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253004"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indeksatory w interfejsach (Przewodnik programowania w języku C#)
Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md). Metody dostępu indeksatorów interfejsów różnią się od metod dostępu indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:  
  
- Metody dostępu interfejsów nie używają modyfikatorów.  
  
- Metoda dostępu do interfejsu nie ma treści.  
  
 W tym celu metoda dostępu wskazuje, czy indeksator jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.  
  
 Oto przykład metody dostępu indeksatora interfejsu:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 Podpis indeksatora musi różnić się od sygnatur wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować indeksatory interfejsów.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 W powyższym przykładzie można użyć jawnej implementacji elementu członkowskiego interfejsu przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu. Na przykład:  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora. Na przykład jeśli `Employee` Klasa implementuje dwa interfejsy `IEmployee`, `ICitizen` a oba interfejsy mają tę samą sygnaturę indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu. Oznacza to, że następująca deklaracja indeksatora:  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementuje indeksator w `IEmployee` interfejsie, podczas gdy następująca deklaracja:  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 implementuje indeksator w `ICitizen` interfejsie.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Indeksatory](./index.md)
- [Właściwości](../classes-and-structs/properties.md)
- [Interfejsy](../interfaces/index.md)
