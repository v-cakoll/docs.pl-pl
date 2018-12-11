---
title: Automatycznie implementowane właściwości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 1277e0908b42b6f8185219a33c2b28537c8b6607
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244196"
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
  
 Atrybuty są dozwolone na automatycznie implementowane właściwości, ale oczywiście nie w polach zapasowy, ponieważ te nie są dostępne z kodu źródłowego. Jeśli musisz użyć atrybutu pola zapasowego właściwości, wystarczy utworzyć regularne właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
