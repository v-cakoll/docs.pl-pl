---
title: Indeksatory w interfejsach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c3ddb48590087d49402482e8cbf3760027da1a2a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799466"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indeksatory w interfejsach (Przewodnik programowania w języku C#)
Można zadeklarować indeksatorów w [interfejsu](../../../csharp/language-reference/keywords/interface.md). Metody dostępu interfejsu indeksatorów różnią się od metod dostępu [klasy](../../../csharp/language-reference/keywords/class.md) indeksatorów w następujący sposób:  
  
-   Metody dostępu interfejsu należy używać modyfikatorów.  
  
-   Metody dostępu interfejsu nie ma treści.  
  
 W związku z tym metody dostępu ma na celu wskazać indeksatora odczytu i zapisu, tylko do odczytu lub tylko do zapisu.  
  
 Oto przykład metody dostępu interfejsu indeksatora:  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 Podpis indeksatora musi się różnić od podpisy innymi indeksatorami zadeklarowanych w tym samym interfejsie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować interfejs indeksatorów.  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 W poprzednim przykładzie można użyć jawną implementacją członków przy użyciu w pełni kwalifikowana nazwa składowej interfejsu. Na przykład:  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 Jednak w pełni kwalifikowana nazwa jest wymagane tylko aby uniknąć niejednoznaczności, implementując klasy jest więcej niż jeden interfejs, za pomocą tego samego podpisu indeksatora. Na przykład jeśli `Employee` klasa implementuje dwa interfejsy `ICitizen` i `IEmployee`, i dotyczą obu interfejsów mają taki sam podpis indeksatora, niezbędne jest jawną implementacją członków. Oznacza to, że następująca deklaracja indeksatora:  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementuje indeksatora na `IEmployee` interfejsu podczas następującą deklarację:  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 implementuje indeksatora na `ICitizen` interfejsu.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
