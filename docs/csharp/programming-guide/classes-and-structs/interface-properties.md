---
title: Właściwości interfejsu (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325412"
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
 [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
