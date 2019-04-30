---
title: C#Interfejsy — Przewodnik po przykładzie C# języka
description: Interfejsy definiują kontraktów implementowany przez typy wC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: bfc6b59a411ff2ddb3331a8bdf24c0ae3d611273
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706406"
---
# <a name="interfaces"></a>Interfejsy

***Interfejsu*** definiuje kontrakt, który może być implementowany przez klas i struktur. Interfejs może zawierać metody, właściwości, zdarzeń i indeksatorów. Interfejs nie zawiera implementacji członków definiuje — jedynie określa elementy członkowskie, które muszą być dostarczane przez klasy lub struktury, które implementują interfejs.

Interfejsy mogą stosować ***wielokrotne dziedziczenie***. W poniższym przykładzie interfejs `IComboBox` dziedziczy z obu `ITextBox` i `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Klasy i struktury można zaimplementować wiele interfejsów. W poniższym przykładzie klasa `EditBox` implementuje interfejsy `IControl` i `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Gdy klasa lub struktura implementuje danego interfejsu, wystąpienia tej klasy lub struktury mogą być niejawnie konwertowane do tego typu interfejsu. Na przykład

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

W przypadkach, gdy wystąpienie nie jest znany statycznie do implementowania określonego interfejsu służy rzutowania typu dynamicznego. Na przykład poniższe instrukcje użyć rzutowania typu dynamicznego do uzyskiwania obiektu `IControl` i `IDataBound` implementacji interfejsu. Ponieważ jest środowiska wykonawczego, rzeczywisty typ obiektu `EditBox`, rzutowania powiodło się.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

W ciągu poprzednich `EditBox` klasy `Paint` metody z `IControl` interfejsu i `Bind` metody z `IDataBound` interfejsu są implementowane przy użyciu publicznych składowych. C#również obsługuje jawnej ***interfejsu implementacji elementu członkowskiego***, umożliwiając klasy lub struktury, aby uniknąć konieczności publiczne elementy członkowskie. Implementacja interfejsu jawnego członka jest zapisywany przy użyciu interfejsu w pełni kwalifikowana nazwa elementu członkowskiego. Na przykład `EditBox` implementacji klasy `IControl.Paint` i `IDataBound.Bind` metod za pomocą jawnych implementacji elementu członkowskiego interfejsu w następujący sposób.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Elementy członkowskie interfejsu jawnego zostać oceniony jedynie przez typ interfejsu. Na przykład implementacji `IControl.Paint` dostarczone przez poprzednie EditBox klasy może być wywoływany tylko przez uprzedniego przekonwertowania `EditBox` odwołanie do `IControl` typ interfejsu.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Poprzednie](arrays.md)
>[dalej](enums.md)