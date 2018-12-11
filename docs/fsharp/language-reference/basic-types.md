---
title: Typy podstawowe (F#)
description: Odkryj podstawowych typów podstawowych, które są używane w F# języka.
ms.date: 07/09/2018
ms.openlocfilehash: a8a1154a211d8c87571b47cb41cb091096569472
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145127"
---
# <a name="basic-types"></a>Typy podstawowe

W tym temacie przedstawiono podstawowe typy, które są zdefiniowane w F# języka. Te typy są zasadnicze znaczenie w F#, stanowiący podstawę prawie w każdym F# program. Są one podzbiorem .NET typów pierwotnych.

|Typ|Typ architektury .NET|Opis|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|Możliwe wartości to `true` i `false`.|
|`byte`|<xref:System.Byte>|Wartości z zakresu od 0 do 255.|
|`sbyte`|<xref:System.SByte>|Wartości od -128 do 127 znaków.|
|`int16`|<xref:System.Int16>|Wartości od -32768 do 32767.|
|`uint16`|<xref:System.UInt16>|Wartości z zakresu od 0 do 65535.|
|`int`|<xref:System.Int32>|Wartości od -2,147,483,648 do 2 147 483 647.|
|`uint32`|<xref:System.UInt32>|Wartości z zakresu od 0 do 4 294 967 295.|
|`int64`|<xref:System.Int64>|Wartości z-9,223,372,036,854,775,808 9,223,372,036,854,775,807.|
|`uint64`|<xref:System.UInt64>|Wartości z zakresu od 0 do 18,446,744,073,709,551,615.|
|`nativeint`|<xref:System.IntPtr>|Wskaźnik natywny jako liczba całkowita ze znakiem.|
|`unativeint`|<xref:System.UIntPtr>|Wskaźnik natywny jako liczba całkowita bez znaku.|
|`char`|<xref:System.Char>|Wartości znakowych Unicode.|
|`string`|<xref:System.String>|Tekst w formacie Unicode.|
|`decimal`|<xref:System.Decimal>|Zmiennoprzecinkowa typ danych, który ma co najmniej 28 cyfr znaczących.|
|`unit`|Nie dotyczy|Wskazuje brak rzeczywistej wartości. Typ ma tylko jedną wartość formalny, która jest oznaczona `()`. Wartość jednostki `()`, jest często używana jako symbol zastępczy, której wartość jest wymagana, ale nie rzeczywistą wartość jest dostępna lub ma sens.|
|`void`|<xref:System.Void>|Wskazuje nie typu lub wartości.|
|`float32`, `single`|<xref:System.Single>|32-bitowych punktu typ zmiennoprzecinkowy.|
|`float`, `double`|<xref:System.Double>|64-bitowych punktu typ zmiennoprzecinkowy.|

> [!NOTE]
> Można wykonać obliczeń na liczbach całkowitych zbyt duży dla typu 64-bitową liczbę całkowitą, przy użyciu [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu. `bigint` nie jest uważany za typu podstawowego; jest skrótem `System.Numerics.BigInteger`.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
