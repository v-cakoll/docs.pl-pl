---
title: Właściwości zaimplementowane przez implementację — Przewodnik programowania w języku C#
description: Dla właściwości automatycznie zaimplementowane w języku C#, zgodność tworzy prywatne, anonimowe pole umożliwiające dostęp tylko za pomocą metody dostępu get i set właściwości.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: f58f9a23f26bde7e80d834528d94e38af1231e7b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474478"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)

W języku C# 3,0 i nowszych właściwości, które są implementowane przez implementację właściwości, są bardziej zwięzłe, gdy w metodzie dostępu do właściwości nie jest wymagana żadna dodatkowa logika. Umożliwiają również tworzenie obiektów przez kod klienta. W przypadku deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe pole zapasowe, do którego można uzyskać dostęp tylko za pomocą właściwości `get` i `set` metod dostępu.
  
## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości, które są implementowane.  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Nie można zadeklarować właściwości, które są implementowane w interfejsach. Wstępnie zaimplementowane właściwości deklarują pole kopii zapasowej wystąpienia prywatnego, a interfejsy nie mogą deklarować pól wystąpień. Deklarowanie właściwości w interfejsie bez definiowania treści deklaruje właściwość z dostępem, które muszą być zaimplementowane przez każdy typ, który implementuje ten interfejs.

W języku C# 6 i nowszych można inicjować właściwości, które zostały zaimplementowane w podobny sposób do pól:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna. Kod klienta może zmienić wartości w obiektach po utworzeniu. W przypadku złożonych klas, które zawierają znaczące zachowanie (metody), jak również dane, często konieczne jest posiadanie właściwości publicznych. Jednakże w przypadku małych klas i struktur, które po prostu hermetyzują zestaw wartości (danych) i mają niewielkie lub nie zachowania, należy sprawić, aby obiekty były niezmienne poprzez zadeklarowanie metody dostępu do zestawu jako [prywatne](../../language-reference/keywords/private.md) (niezmiennych dla konsumentów) lub przez zadeklarowanie tylko metody dostępu get (niezmiennej wszędzie poza konstruktorem).  Aby uzyskać więcej informacji, zobacz [jak zaimplementować klasę uproszczoną z właściwościami, które są implementowane](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Zobacz także

- [Właściwości](./properties.md)
- [Modyfikatory](/dotnet/csharp/language-reference/keywords)
