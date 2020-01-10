---
title: Jak jawnie zaimplementować członków interfejsu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d006db2a7501a3273f5cd11e82bc589b21e1ce9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712094"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Jak jawnie zaimplementować członków interfejsu (C# Przewodnik programowania)
Ten przykład deklaruje [interfejs](../../language-reference/keywords/interface.md), `IDimensions`i klasę `Box`, która jawnie implementuje elementy członkowskie interfejsu `getLength` i `getWidth`. Dostęp do członków uzyskuje się za pomocą wystąpienia interfejsu `dimensions`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
  
- Zwróć uwagę, że następujące wiersze w metodzie `Main` są oznaczane jako komentarze, ponieważ spowodują błędy kompilacji. Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Zwróć również uwagę, że następujące wiersze w metodzie `Main` pomyślnie wydrukowały Wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Jak jawnie zaimplementować członków dwóch interfejsów](./how-to-explicitly-implement-members-of-two-interfaces.md)
