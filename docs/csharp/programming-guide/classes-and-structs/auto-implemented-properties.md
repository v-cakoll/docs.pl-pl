---
title: Automatycznie implementowane właściwości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef9243498f3f97e560e45c389932ff57e1e4eef7
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058519"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)
W języku C# 3.0 i nowszych wersjach automatycznie implementowane właściwości należy deklaracja właściwości bardziej zwięzły widok żądanie nie dodatkowej logiki w metodach dostępu właściwości. Umożliwiają one również kod klienta do tworzenia obiektów. Kiedy Deklarujesz właściwości, jak pokazano w poniższym przykładzie, kompilator utworzy polem zapasowym prywatne i anonimowy, który jest możliwy tylko za pośrednictwem właściwości `get` i `set` metod dostępu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje prosty klasy, która ma kilka właściwości zaimplementowane automatycznie:  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 W języku C# 6 lub nowszej można zainicjować właściwości zaimplementowane automatycznie, podobnie jak pola:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna. Kod klienta można zmienić wartości w obiektach, po ich utworzeniu. W klasach złożonych, które zawierają istotne zachowanie (metod) oraz danych często jest konieczne właściwości publiczne. Jednak dla małych klas lub struktur, które po prostu hermetyzacji zestaw wartości (dane) i ma niewielkiego lub żadnego zachowań, albo należy obiekty niezmienne przez zadeklarowanie metody dostępu set jako [prywatnej](../../../csharp/language-reference/keywords/private.md) (niezmienne konsumentom) lub przez deklarowanie tylko akcesor pobierania (niezmienne wszędzie z wyjątkiem konstruktora).  Aby uzyskać więcej informacji, zobacz [jak: Implementowanie klasy Lightweight przy użyciu automatycznie implementowanych właściwości](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
## <a name="see-also"></a>Zobacz też

- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
