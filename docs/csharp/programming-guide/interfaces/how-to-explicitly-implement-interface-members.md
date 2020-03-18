---
title: Jak jawnie implementować elementy członkowskie interfejsu - Przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627788"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Jak jawnie implementować elementy członkowskie interfejsu (Przewodnik programowania Języka C#)
W tym przykładzie [interface](../../language-reference/keywords/interface.md)deklaruje `IDimensions`interfejs , `Box`i klasy , który jawnie implementuje elementy członkowskie `GetLength` interfejsu i `GetWidth`. Elementy członkowskie są dostępne za `dimensions`pośrednictwem wystąpienia interfejsu .  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
- Należy zauważyć, że następujące `Main` wiersze, w metodzie, są komentowane, ponieważ mogą one powodować błędy kompilacji. Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy:](../../language-reference/keywords/class.md)  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Należy również zauważyć, że `Main` następujące wiersze w metodzie pomyślnie wydrukować wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Jawne implementowanie elementów dwóch interfejsów](./how-to-explicitly-implement-members-of-two-interfaces.md)
