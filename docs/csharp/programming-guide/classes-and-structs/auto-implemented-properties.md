---
title: "Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1aa923c6d8208c2d5451957c4112493d0acd561d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)
W języku C# 3.0 lub nowszej automatycznie implementowane właściwości należy deklaracja właściwości bardziej zwięzły gdy wymagany jest nie dodatkową logikę w akcesorach właściwości. Umożliwiają one również kod klienta do tworzenia obiektów. Jak pokazano w poniższym przykładzie w deklaracji właściwości, kompilator tworzy polem zapasowym prywatne i anonimowy, który jest możliwy tylko za pośrednictwem właściwości `get` i `set` metody dostępu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono prosty klasy, która ma niektórych właściwości zaimplementowane automatycznie:  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 W języku C# 6 i nowsze można zainicjować właściwości zaimplementowane automatycznie, podobnie jak pola:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna. Kod klienta można zmienić wartości w obiektach, po ich utworzeniu. W złożonych klasy, które zawierają istotne zachowanie (metody) oraz dane jest często konieczne właściwości publiczne. Jednak dla małych klasy lub struktury, po prostu Hermetyzowanie zbiór wartości (dane) i mieć żadnych zachowań, albo należy obiekty niezmienne przez zadeklarowanie metody dostępu set jako [prywatnej](../../../csharp/language-reference/keywords/private.md) (niezmienne konsumentom) lub przez deklarowanie akcesora get (niezmienne wszędzie, z wyjątkiem konstruktora).  Aby uzyskać więcej informacji, zobacz [porady: Implementowanie klasy Lightweight przy użyciu właściwości Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Atrybuty są dozwolone na właściwości zaimplementowane automatycznie, ale oczywiście nie na pola zapasowy, ponieważ te nie są dostępne z kodu źródłowego. Jeśli atrybut musi być używany dla pola zapasowy właściwości, wystarczy utworzyć regularne właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
