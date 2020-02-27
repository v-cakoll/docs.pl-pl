---
title: Jak jawnie zaimplementować członków interfejsu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627788"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Jak jawnie zaimplementować członków interfejsu (C# Przewodnik programowania)
Ten przykład deklaruje [interfejs](../../language-reference/keywords/interface.md), `IDimensions`i klasę `Box`, która jawnie implementuje elementy członkowskie interfejsu `GetLength` i `GetWidth`. Dostęp do członków uzyskuje się za pomocą wystąpienia interfejsu `dimensions`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
- Zwróć uwagę, że następujące wiersze w metodzie `Main` są oznaczane jako komentarze, ponieważ spowodują błędy kompilacji. Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Zwróć również uwagę, że następujące wiersze w metodzie `Main` pomyślnie wydrukowały Wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Jak jawnie zaimplementować członków dwóch interfejsów](./how-to-explicitly-implement-members-of-two-interfaces.md)
