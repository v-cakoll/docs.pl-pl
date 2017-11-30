---
title: "Właściwości interfejsu (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1da48adf73cccb28d9cff641948db52b40b8c1bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interface-properties-c-programming-guide"></a>Właściwości interfejsu (Przewodnik programowania w języku C#)
Właściwości mogą być deklarowane w [interfejsu](../../../csharp/language-reference/keywords/interface.md). Poniżej przedstawiono przykład metody dostępu interfejsu indeksatora:  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 Metody dostępu właściwości interfejsu nie ma treści. W związku z tym celem metody dostępu jest wskazuje, czy właściwość jest do odczytu / zapisu, tylko do odczytu lub tylko do zapisu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie interfejs `IEmployee` ma właściwość odczytu i zapisu, `Name`, a właściwość tylko do odczytu, `Counter`. Klasa `Employee` implementuje `IEmployee` interfejsu i używa te dwie właściwości. Program odczytuje nazwę nowych pracowników i bieżącą liczbę pracowników i wyświetla nazwę pracowników i numer obliczona pracownika.  
  
 Można użyć w pełni kwalifikowana nazwa właściwość, która odwołuje się do interfejsu, w którym zadeklarowano ten element członkowski. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Ta metoda jest wywoływana [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Na przykład jeśli klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i dotyczą obu interfejsów `Name` właściwość, implementacja interfejsu jawnego członka będzie to konieczne. Oznacza to, że następujące deklaracja właściwości:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implementuje `Name` właściwość `IEmployee` interfejsu podczas następujące oświadczenie:  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 implementuje `Name` właściwość `ICitizen` interfejsu.  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Przy użyciu właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
