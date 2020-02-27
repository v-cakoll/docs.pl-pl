---
title: Zaimplementowane właściwości — C# Przewodnik programowania
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 989266bfc2de9bd5ce2948f09a2b9f19dd2c782e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628296"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Właściwości zaimplementowane automatycznie (Przewodnik programowania w języku C#)

W C# 3,0 i nowszych właściwości, które są implementowane przez funkcję właściwości, są bardziej zwięzłe, gdy w metodzie dostępu do właściwości nie jest wymagana żadna dodatkowa logika. Umożliwiają również tworzenie obiektów przez kod klienta. W przypadku deklarowania właściwości, jak pokazano w poniższym przykładzie, kompilator tworzy prywatne, anonimowe pole zapasowe, do którego można uzyskać dostęp tylko za pomocą `get` i `set` metod dostępu.
  
## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono prostą klasę, która ma pewne właściwości, które są implementowane.  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Nie można zadeklarować właściwości, które są implementowane w interfejsach. Wstępnie zaimplementowane właściwości deklarują pole kopii zapasowej wystąpienia prywatnego, a interfejsy nie mogą deklarować pól wystąpień. Deklarowanie właściwości w interfejsie bez definiowania treści deklaruje właściwość z dostępem, które muszą być zaimplementowane przez każdy typ, który implementuje ten interfejs.

W C# 6 i nowszych można inicjować właściwości zaimplementowane w sposób podobny do pól:  
 
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
 
Klasa, która jest wyświetlana w poprzednim przykładzie jest modyfikowalna. Kod klienta może zmienić wartości w obiektach po utworzeniu. W przypadku złożonych klas, które zawierają znaczące zachowanie (metody), jak również dane, często konieczne jest posiadanie właściwości publicznych. Jednakże w przypadku małych klas i struktur, które po prostu hermetyzują zestaw wartości (danych) i mają niewielkie lub nie zachowania, należy sprawić, aby obiekty były niezmienne poprzez zadeklarowanie metody dostępu do zestawu jako [prywatne](../../language-reference/keywords/private.md) (niezmiennych dla konsumentów) lub przez zadeklarowanie tylko metody dostępu get (niezmiennej wszędzie poza konstruktorem).  Aby uzyskać więcej informacji, zobacz [jak zaimplementować klasę uproszczoną z właściwościami, które są implementowane](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Zobacz też

- [Właściwości](./properties.md)
- [Modyfikatory](/dotnet/csharp/language-reference/keywords)
