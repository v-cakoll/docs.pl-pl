---
title: Indeksatory w interfejsach C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 4ac51589ed1680f8484fde797c045d15beed3af9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712120"
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
  
 Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora. Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy, `ICitizen` i `IEmployee`, a oba interfejsy mają ten sam podpis indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu. Oznacza to, że następująca deklaracja indeksatora:  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementuje indeksator w interfejsie `IEmployee`, podczas gdy następująca deklaracja:  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 implementuje indeksator w interfejsie `ICitizen`.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Indeksatory](./index.md)
- [Właściwości](../classes-and-structs/properties.md)
- [Interfejsy](../interfaces/index.md)
