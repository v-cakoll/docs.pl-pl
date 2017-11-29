---
title: Typy pierwotne (F#)
description: "Poznaj podstawowe typy pierwotne, które są używane w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a>Typy pierwotne

Ten temat zawiera podstawowe typy pierwotne, które są używane w języku F #. Dla każdego typu danych umożliwia także odpowiednie typy .NET i wartości minimalną i maksymalną.

## <a name="summary-of-primitive-types"></a>Podsumowanie typów pierwotnych
Poniższa tabela zawiera podsumowanie właściwości pierwotnych typów F #.

|Typ|Typ architektury .NET|Opis|
|----|---------|-----------|
|`bool`|`System.Boolean`|Możliwe wartości to `true` i `false`.|
|`byte`|`System.Byte`|Wartości z zakresu od 0 do 255.|
|`sbyte`|`System.SByte`|Wartości od -128 do 127 znaków.|
|`int16`|`System.Int16`|Wartości od -32768 do 32767.|
|`uint16`|`System.UInt16`|Wartości z zakresu od 0 do 65535.|
|`int`|`System.Int32`|Wartości od -2,147,483,648 do 2 147 483 647.|
|`uint32`|`System.UInt32`|Wartości z zakresu od 0 do 4 294 967 295.|
|`int64`|`System.Int64`|Wartości od-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807.|
|`uint64`|`System.UInt64`|Wartości z zakresu od 0 do 18,446,744,073,709,551,615.|
|`nativeint`|`System.IntPtr`|Wskaźnik natywny jako liczbę całkowitą ze znakiem.|
|`unativeint`|`System.UIntPtr`|Wskaźnik natywny jako liczba całkowita bez znaku.|
|`char`|`System.Char`|Wartości znakowych Unicode.|
|`string`|`System.String`|Tekst Unicode.|
|`decimal`|`System.Decimal`|Zmiennoprzecinkowa typ danych, który ma co najmniej 28 cyfr znaczących.|
|`unit`|Nie dotyczy|Wskazuje brak rzeczywistą wartość. Typ ma tylko jeden formalny wartość, która jest oznaczona `()`. Wartość jednostki `()`, jest często używana jako symbol zastępczy, gdy wartość jest wymagana, ale nie rzeczywistą wartość jest dostępna lub ma sens.|
|`void`|`System.Void`|Wskazuje nie typem lub wartością.|
|`float32, single`|`System.Single`|32-bitowych zmiennoprzecinkowych punktu typu.|
|`float, double`|`System.Double`|64-bitowych zmiennoprzecinkowych punktu typu.|

>[!NOTE]
Można wykonać obliczenia z liczb całkowitych za duża dla typu 64-bitową liczbę całkowitą przy użyciu [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu. `bigint`nie jest uznawany za typ pierwotny; jest skrótem `System.Numerics.BigInteger`.

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)
