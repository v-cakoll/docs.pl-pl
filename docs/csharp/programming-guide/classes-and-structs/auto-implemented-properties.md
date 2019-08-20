---
title: Zaimplementowane właściwości — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 44f3beb9de8c9d339c42db26bb9c510998abc7d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597138"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)
W C# 3,0 i nowszych właściwości, które są implementowane przez funkcję właściwości, są bardziej zwięzłe, gdy w metodzie dostępu do właściwości nie jest wymagana żadna dodatkowa logika. Umożliwiają również tworzenie obiektów przez kod klienta. W przypadku deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe pole zapasowe, do którego można uzyskać dostęp tylko za pomocą `get` właściwości `set` i metod dostępu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości, które są implementowane.  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 W C# 6 i nowszych można inicjować właściwości zaimplementowane w sposób podobny do pól:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna. Kod klienta może zmienić wartości w obiektach po ich utworzeniu. W przypadku złożonych klas, które zawierają znaczące zachowanie (metody), jak również dane, często konieczne jest posiadanie właściwości publicznych. Jednakże w przypadku małych klas i struktur, które po prostu hermetyzują zestaw wartości (danych) i mają niewielkie lub bez zachowań, należy sprawić, aby obiekty były niezmienne poprzez zadeklarowanie metody dostępu do zestawu jako [prywatne](../../language-reference/keywords/private.md) (niezmiennych dla konsumentów) lub przez zadeklarowanie tylko Get Metoda dostępu (niezmiennej wszędzie poza konstruktorem).  Aby uzyskać więcej informacji, zobacz [jak: Zaimplementuj klasę uproszczoną z właściwościami](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md), które są implementowane.  
  
## <a name="see-also"></a>Zobacz także

- [Właściwości](./properties.md)
- [Modyfikatory](../../language-reference/keywords/modifiers.md)
