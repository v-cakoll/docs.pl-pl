---
title: Wyliczanie ciągów formatujących — .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2e5dbe0d02bcec8974a1e52c0dce107d3bf46b
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052852"
---
# <a name="enumeration-format-strings"></a>Wyliczanie ciągów formatujących

Możesz użyć <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć nowy obiekt ciągu reprezentujący liczbowy, szesnastkowo lub wartości ciągu elementu członkowskiego wyliczenia. Ta metoda przyjmuje jeden wyliczenie formatowanie ciągów, aby określić wartości, które mają być zwracane.

W poniższych sekcjach wymieniono wyliczenie formatowanie ciągów i wartości, które zwracają. Te specyfikatory formatu nie jest rozróżniana wielkość liter.

## <a name="g-or-g"></a>G lub g

Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe, a w przeciwnym razie wyświetlana jest wartość całkowitą bieżącego wystąpienia. Jeśli nie zdefiniowano wyliczenia z **flagi** zestaw atrybutów, ciąg wartości każdego prawidłowego wpisu są łączone ze sobą, oddzielonych przecinkami. Jeśli **flagi** atrybut nie jest ustawiony, nieprawidłową wartość jest wyświetlana jako wpisy numeryczne. Poniższy przykład ilustruje specyfikator formatu G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F lub f

Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe. Jeśli wartość, które mogą być całkowicie wyświetlane jako suma pozycji w wyliczeniu (nawet wtedy, gdy **flagi** atrybut nie jest obecny), wartości ciągu każdego wpisu prawidłowe są połączone ze sobą, oddzielonych przecinkami. Jeśli wartość nie może całkowicie określana przez wpisy wyliczenie, wartość jest formatowana jako wartość całkowitą. Poniższy przykład ilustruje specyfikator formatu F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D lub d

Wyświetla wpis wyliczenia jako wartość całkowitą w możliwie najkrótszym reprezentacji możliwe. Poniższy przykład ilustruje specyfikator formatu D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X lub x

Wyświetla wpis wyliczenia jako wartość szesnastkową. Wartość jest reprezentowana z zerami zgodnie z potrzebami upewnić się, że ciąg wynikowy ma dwa znaki dla każdego bajtu w typ wyliczeniowy [bazowy typ liczbowy](xref:System.Enum.GetUnderlyingType%2A). Poniższy przykład ilustruje specyfikator formatu X. W tym przykładzie typ podstawowy elementu zarówno <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> jest <xref:System.Int32>, lub 32-bitowego (lub 4-bajtowych) całkowitą, która tworzy ciąg wyniku 8 znaków.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano wyliczenia zwanego `Colors` składający się z trzech wpisów: `Red`, `Blue`, i `Green`.

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Po zdefiniowaniu wyliczenia wystąpienie może być zadeklarowana w następujący sposób.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

`Color.ToString(System.String)` Metoda następnie może służyć do wyświetlania wartości wyliczenia na różne sposoby, w zależności od specyfikatora formatu przekazane do niego.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Zobacz także

- [Formatowanie typów](formatting-types.md)
