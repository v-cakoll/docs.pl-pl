---
title: 'Instrukcje: Jawne implementowanie elementów członkowskich C# interfejsu — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589208"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Instrukcje: Jawnie Implementuj elementy członkowskie interfejsuC# (Przewodnik programowania)
Ten przykład deklaruje [interfejs](../../language-reference/keywords/interface.md), `IDimensions`i klasę, `Box`, która jawnie implementuje elementy członkowskie `getLength` interfejsu i `getWidth`. Dostęp do członków uzyskuje się za pomocą `dimensions`wystąpienia interfejsu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
- Zwróć uwagę, że następujące wiersze w metodzie są oznaczone jako `Main` komentarze, ponieważ spowodują błędy kompilacji. Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Zwróć również uwagę, że w `Main` metodzie pomyślnie Wydrukowano Wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsów](./how-to-explicitly-implement-members-of-two-interfaces.md)
