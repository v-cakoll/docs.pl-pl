---
title: C#Interfejsy — Przewodnik po C# języku
description: Interfejsy definiują kontrakty zaimplementowane przez typy wC#
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159133"
---
# <a name="interfaces"></a>Interfejsy

***Interfejs*** definiuje kontrakt, który może być zaimplementowany przez klasy i struktury. Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory. Interfejs nie zapewnia implementacji elementów członkowskich, które definiuje — tylko określa elementy członkowskie, które muszą być dostarczone przez klasy lub struktury, które implementują interfejs.

Interfejsy mogą wykorzystywać ***wielokrotne dziedziczenie***. W poniższym przykładzie interfejs `IComboBox` dziedziczy po obu `ITextBox` i `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Klasy i struktury mogą implementować wiele interfejsów. W poniższym przykładzie Klasa `EditBox` implementuje obu `IControl` i `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Gdy Klasa lub struktura implementuje określony interfejs, wystąpienia tej klasy lub struktury mogą być niejawnie konwertowane na typ tego interfejsu. Na przykład

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

W przypadkach, gdy wystąpienie nie jest statycznie znane do implementacji określonego interfejsu, można użyć rzutowania typu dynamicznego. Na przykład następujące instrukcje używają rzutowania typu dynamicznego do uzyskiwania `IControl` i implementacji interfejsu `IDataBound`. Ponieważ rzeczywisty typ obiektu jest `EditBox`, rzutowania powiodło się.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

W poprzedniej klasie `EditBox` Metoda `Paint` z interfejsu `IControl` oraz Metoda `Bind` z interfejsu `IDataBound` są implementowane przy użyciu publicznych członków. C#obsługuje również jawne ***implementacje elementu członkowskiego interfejsu***, co pozwala klasie lub strukturze uniknąć udostępniania elementów członkowskich publicznie. Implementacja jawnego elementu członkowskiego interfejsu jest zapisywana przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu. Na przykład Klasa `EditBox` może zaimplementować metody `IControl.Paint` i `IDataBound.Bind` przy użyciu jawnych implementacji elementu członkowskiego interfejsu w następujący sposób.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Dostęp do jawnych elementów członkowskich interfejsu można uzyskać tylko za pośrednictwem typu interfejsu. Na przykład implementacja `IControl.Paint` dostarczonej przez poprzednią klasę EditBox można wywołać tylko przez pierwsze przekonwertowanie odwołania `EditBox` do typu interfejsu `IControl`.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Poprzednie](arrays.md)
>[dalej](delegates.md)
