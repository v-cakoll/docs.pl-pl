---
title: Właściwości interfejsu — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: cdd425970442e284d6fd6488bbb13394c12e939a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596451"
---
# <a name="interface-properties-c-programming-guide"></a>Właściwości interfejsu (Przewodnik programowania w języku C#)
Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md). Oto przykład metody dostępu do właściwości interfejsu:  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 Metoda dostępu do właściwości interfejsu nie ma treści. W tym celu metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie interfejs `IEmployee` ma `Name`właściwość do odczytu i zapisu oraz właściwość tylko do `Counter`odczytu. `Employee` Klasa`IEmployee` implementuje interfejs i używa tych dwóch właściwości. Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.  
  
 Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski. Na przykład:  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 Ta nazwa jest nazywana [jawnym implementacją interfejsu](../interfaces/explicit-interface-implementation.md). `Employee` Na przykład jeśli klasa implementuje dwa interfejsy `ICitizen` i `IEmployee` oba interfejsy mają `Name` właściwość, wymagana jest Jawna implementacja elementu członkowskiego interfejsu. Oznacza to, że następująca deklaracja właściwości:  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 `Name` implementuje właściwość `IEmployee` w interfejsie, podczas gdy następująca deklaracja:  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 `Name` implementuje właściwość `ICitizen` w interfejsie.  
  
 [!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Używanie właściwości](./using-properties.md)
- [Porównanie właściwości i indeksatorów](../indexers/comparison-between-properties-and-indexers.md)
- [Indeksatory](../indexers/index.md)
- [Interfejsy](../interfaces/index.md)
