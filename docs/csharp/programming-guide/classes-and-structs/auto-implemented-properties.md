---
title: Właściwości implementowane automatycznie — przewodnik programowania C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170328"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)

W języku C# 3.0 i nowszych właściwości auto-implemented dokonać deklaracji właściwości bardziej zwięzłe, gdy nie dodatkowe logiki jest wymagane w akcesorów właściwości. Umożliwiają one również kod klienta do tworzenia obiektów. Podczas deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe `get` `set` pole zapasowe, które jest dostępne tylko za pośrednictwem właściwości i akcesorów.
  
## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości implementowane automatycznie:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Nie można zadeklarować właściwości zaimplementowane automatycznie w interfejsach. Właściwości implementowane automatycznie deklarują pole zapasowe wystąpienia prywatnego, a interfejsy mogą nie deklarować pól wystąpienia. Deklarowanie właściwości w interfejsie bez definiowania treści deklaruje właściwość z akcesorami, które muszą być implementowane przez każdy typ, który implementuje ten interfejs.

W języku C# 6 i nowszych można zainicjować właściwości implementowane automatycznie podobnie do pól:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Klasa, która jest pokazana w poprzednim przykładzie jest zmienna. Kod klienta można zmienić wartości w obiektach po utworzeniu. W złożonych klas, które zawierają znaczące zachowanie (metody), a także dane, często jest konieczne, aby mieć właściwości publiczne. Jednak dla małych klas lub struktur, które po prostu hermetyzują zestaw wartości (dane) i mają niewiele lub nie ma zachowań, należy albo zrobić obiekty niezmienne, deklarując set akcesor jako [prywatny](../../language-reference/keywords/private.md) (niezmienne dla konsumentów) lub deklarując tylko get akcesor (niezmienne wszędzie z wyjątkiem konstruktora).  Aby uzyskać więcej informacji, zobacz [Jak zaimplementować klasę lekką z właściwościami implementowanymi automatycznie](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Zobacz też

- [Właściwości](./properties.md)
- [Modyfikatory](/dotnet/csharp/language-reference/keywords)
