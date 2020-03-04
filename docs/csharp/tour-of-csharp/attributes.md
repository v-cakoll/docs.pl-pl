---
title: C#Atrybuty — przewodnik po C# języku
description: Dowiedz się więcej na temat programowania deklaracyjnego przy użyciu atrybutów wC#
ms.date: 02/27/2020
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: dc5b194c22fc2746ff8b0ab3e550e560a3666bbe
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159211"
---
# <a name="attributes"></a>Atrybuty

Typy, elementy członkowskie i inne jednostki w C# programie obsługują Modyfikatory kontrolujące pewne aspekty ich zachowania. Na przykład dostępność metody jest kontrolowana przy użyciu modyfikatorów `public`, `protected`, `internal`i `private`. C#służy do uogólniania tej funkcji w taki sposób, aby typy informacji deklaratywnych zdefiniowanych przez użytkownika mogły być dołączane do jednostek programu i pobierane w czasie wykonywania. Programy określają te dodatkowe informacje deklaracyjne przez definiowanie i używanie ***atrybutów***.

Poniższy przykład deklaruje `HelpAttribute` atrybutu, który może być umieszczony w jednostkach programu, aby udostępnić linki do powiązanej dokumentacji.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Wszystkie klasy atrybutów pochodzą z klasy bazowej <xref:System.Attribute> dostarczonej przez bibliotekę standardową. Atrybuty mogą być stosowane, dając ich nazwę, wraz z dowolnymi argumentami, wewnątrz nawiasów kwadratowych tuż przed skojarzoną deklaracją. Jeśli nazwa atrybutu zostanie zakończona w `Attribute`, ta część nazwy może zostać pominięta, gdy odwołanie do atrybutu. Na przykład `HelpAttribute` może być używana w następujący sposób.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Ten przykład dołącza `HelpAttribute` do klasy `Widget`. Dodaje kolejną `HelpAttribute` do metody `Display` w klasie. Publiczne konstruktory klasy atrybutów kontrolują informacje, które muszą być dostarczone, gdy atrybut jest dołączony do jednostki programu. Dodatkowe informacje można uzyskać, odwołując się do właściwości publicznego odczytu i zapisu klasy atrybutów (takich jak odwołanie do właściwości `Topic` wcześniej).

Metadane zdefiniowane przez atrybuty mogą być odczytywane i manipulowane w czasie wykonywania przy użyciu odbicia. Gdy określony atrybut jest żądany przy użyciu tej techniki, Konstruktor klasy atrybutu jest wywoływany z informacjami podanymi w źródle programu i zwracane jest wystąpienie atrybutu wynikowego. Jeśli dodatkowe informacje zostały przekazane za pomocą właściwości, te właściwości są ustawiane na podane wartości przed zwróceniem wystąpienia atrybutu.

Poniższy przykład kodu demonstruje, jak uzyskać `HelpAttribute` wystąpienia skojarzone z klasą `Widget` i jej metodą `Display`.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Wstecz](delegates.md)
