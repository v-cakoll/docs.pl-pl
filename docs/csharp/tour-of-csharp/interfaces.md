---
title: C# Interfaces — przewodnik po języku Języka C#
description: 'Interfejsy definiują kontrakty implementowane według typów w języku C #'
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159133"
---
# <a name="interfaces"></a>Interfejsy

***Interfejs*** definiuje kontrakt, który może być implementowany przez klasy i struktury. Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory. Interfejs nie zapewnia implementacje elementów członkowskich definiuje — określa jedynie elementy członkowskie, które muszą być dostarczane przez klasy lub struktury, które implementują interfejs.

Interfejsy mogą wykorzystywać ***wiele dziedziczenia***. W poniższym przykładzie `IComboBox` interfejs dziedziczy z obu `ITextBox` i `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Klasy i struktury można zaimplementować wiele interfejsów. W poniższym przykładzie `EditBox` klasa implementuje zarówno `IControl` i `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Gdy klasa lub struktura implementuje określony interfejs, wystąpienia tej klasy lub struktury mogą być niejawnie konwertowane na ten typ interfejsu. Na przykład:

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

W przypadkach, gdy wystąpienie nie jest statycznie znane do zaimplementowania określonego interfejsu, rzutowania typu dynamicznego mogą być używane. Na przykład następujące instrukcje użyć rzutowania typu dynamicznego, aby uzyskać implementacje obiektu `IControl` i `IDataBound` interfejsu. Ponieważ rzeczywisty typ obiektu w czasie `EditBox`wykonywania jest , rzuty powiedzie się.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

W `EditBox` poprzedniej klasie `Paint` metoda `IControl` z interfejsu `Bind` i `IDataBound` metoda z interfejsu są implementowane przy użyciu elementów członkowskich publicznych. C# obsługuje również ***implementacje elementu członkowskiego interfejsu***jawnego, umożliwiając klasy lub struktury, aby uniknąć upubliczniania elementów członkowskich. Implementacja elementu członkowskiego interfejsu jawnego jest zapisywana przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu. Na przykład `EditBox` klasa może `IControl.Paint` implementować i `IDataBound.Bind` metody przy użyciu implementacji elementu członkowskiego interfejsu jawnego w następujący sposób.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Elementy członkowskie interfejsu jawne są dostępne tylko za pośrednictwem typu interfejsu. Na przykład implementacji `IControl.Paint` dostarczonych przez poprzednią klasę EditBox można wywołać tylko przez pierwsze konwertowanie `EditBox` odwołania do typu `IControl` interfejsu.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Poprzedni](arrays.md)
>[następny](delegates.md)
