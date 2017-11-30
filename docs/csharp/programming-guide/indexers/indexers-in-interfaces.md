---
title: "Indeksatory w interfejsach (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 304f2e037d8df025376d06f229ddd1584f8713b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indeksatory w interfejsach (Przewodnik programowania w języku C#)
Można zadeklarować indeksatorów w [interfejsu](../../../csharp/language-reference/keywords/interface.md). Metod dostępu interfejsu indeksatory różnią się od metod dostępu z [klasy](../../../csharp/language-reference/keywords/class.md) indeksatorów w następujący sposób:  
  
-   Metody dostępu interfejsu nie należy używać modyfikatorów.  
  
-   Metody dostępu interfejsu nie ma treści.  
  
 W związku z tym celem metody dostępu jest informujące o powodzeniu indeksatora odczytu i zapisu, tylko do odczytu lub tylko do zapisu.  
  
 Poniżej przedstawiono przykład metody dostępu interfejsu indeksatora:  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 Podpis indeksatora musi różnić się od podpisy innymi indeksatorami zadeklarowany w tym samym interfejsie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do zaimplementowania interfejsu indeksatorów.  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 W poprzednim przykładzie możesz użyć implementacja interfejsu jawnego członka za pomocą w pełni kwalifikowana nazwa elementu członkowskiego interfejsu. Na przykład:  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 Jednak w pełni kwalifikowana nazwa wymagana jest tylko do uniknąć niejednoznaczności, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora. Na przykład jeśli `Employee` klasa implementuje dwa interfejsy `ICitizen` i `IEmployee`, i dotyczą obu interfejsów mają taką samą sygnaturę indeksatora, konieczne jest jawną implementacją elementu interfejsu. Oznacza to, że następujące oświadczenie indeksatora:  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 implementuje indeksatora na `IEmployee` interfejsu podczas następujące oświadczenie:  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 implementuje indeksatora na `ICitizen` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
