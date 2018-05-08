---
title: Interfejsy języka C# — samouczek języka C#
description: Interfejsy Definiowanie kontraktów zaimplementowanych przez typy w języku C#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 0ad02d5b2792656783d93b2cc767aeb81efbc30e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interfaces"></a>Interfejsy

***Interfejsu*** definiuje kontrakt może być zaimplementowany przez klasy i struktury. Interfejs może zawierać metod, właściwości, zdarzeń i indeksatorów. Interfejs nie zawiera implementacji elementów członkowskich definiuje — Określa on tylko elementy członkowskie, które muszą zostać dostarczone przez klasy lub struktury, który implementuje interfejs.

Interfejsy mogą stosować ***dziedziczenie wielokrotne***. W poniższym przykładzie interfejsu `IComboBox` dziedziczy z obu `ITextBox` i `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Klasy i struktury można zaimplementować wiele interfejsów. W poniższym przykładzie klasa `EditBox` implementuje zarówno `IControl` i `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Po klasie lub strukturze implementuje konkretnego interfejsu, wystąpień tej klasy lub struktury można niejawnie przekonwertowana na typ tego interfejsu. Na przykład

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

W przypadkach, gdy wystąpienie jest statycznie nieznany do zaimplementowania konkretnego interfejsu można użyć rzutowania typów dynamicznych. Na przykład następujące instrukcje umożliwia rzutowania z typu dynamicznego uzyskanie obiektu `IControl` i `IDataBound` implementacji interfejsu. Ponieważ środowiska wykonawczego rzeczywisty typ obiektu to `EditBox`, rzutowania powiodło się.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

W poprzednim `EditBox` klasy `Paint` metody z `IControl` interfejsu i `Bind` metody z `IDataBound` interfejsu są implementowane za pomocą publiczne elementy członkowskie. C# obsługuje również jawne ***implementacje elementów członkowskich interfejsu***, włączanie klasy lub struktury, aby uniknąć publiczne elementy członkowskie. Implementacja interfejsu jawnego członka jest zapisywany przy użyciu interfejsu w pełni kwalifikowaną nazwę elementu członkowskiego. Na przykład `EditBox` można zaimplementować klasy `IControl.Paint` i `IDataBound.Bind` metody za pomocą jawnego interfejsu implementacje elementów członkowskich w następujący sposób.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Elementy członkowskie interfejsu jawnego można uzyskać tylko za pośrednictwem typu interfejsu. Na przykład stosowania `IControl.Paint` dostarczane przez poprzednie pole edycji można wywołać tylko klasy konwertując pierwszy `EditBox` odwołanie do `IControl` typu interfejsu.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
[Poprzednie](arrays.md)
[dalej](enums.md)
