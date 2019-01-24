---
title: Właściwości — interfejsu C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: af80f403942f59d672854c80830e175ef7ebaff5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652192"
---
# <a name="interface-properties-c-programming-guide"></a>Właściwości interfejsu (Przewodnik programowania w języku C#)
Właściwości mogą być deklarowane na [interfejsu](../../../csharp/language-reference/keywords/interface.md). Oto przykład metody dostępu właściwości interfejsu:  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 Metoda dostępu właściwość interfejsu nie ma treści. W związku z tym celem metody dostępu jest wskazuje, czy właściwość jest odczytu i zapisu, tylko do odczytu lub tylko do zapisu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie interfejs `IEmployee` ma właściwość odczytu i zapisu, `Name`, a właściwość tylko do odczytu `Counter`. Klasa `Employee` implementuje `IEmployee` interfejs i korzysta z tych dwóch właściwości. Program odczytuje nazwę nowego pracownika i bieżącą liczbę pracowników i wyświetla nazwę pracowników i liczba pracowników obliczanej.  
  
 Można użyć w pełni kwalifikowaną nazwę właściwości, która odwołuje się do interfejsu, w którym zadeklarowany jest element członkowski. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 Jest to nazywane [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md). Na przykład jeśli klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i dotyczą obu interfejsów `Name` właściwości jawną implementacją członków będzie to konieczne. Oznacza to, że następująca deklaracja właściwości:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 implementuje `Name` właściwość `IEmployee` interfejsu podczas następującą deklarację:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Używanie właściwości](../../../csharp/programming-guide/classes-and-structs/using-properties.md)
- [Porównanie właściwości i indeksatorów](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)
- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
