---
title: Wyliczanie ciągów formatujących
description: Utwórz ciągi formatujące Wyliczenie przy użyciu metody enum. ToString w programie .NET. Formatowanie wartości liczbowych, szesnastkowych lub ciągów elementów członkowskich wyliczenia.
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
ms.openlocfilehash: 825357cf4a56132dae0870972d316eff89b0c94f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583430"
---
# <a name="enumeration-format-strings"></a>Wyliczanie ciągów formatujących

Możesz użyć metody, <xref:System.Enum.ToString%2A?displayProperty=nameWithType> Aby utworzyć nowy obiekt ciągu, który reprezentuje wartość liczbową, szesnastkową lub ciąg elementu członkowskiego wyliczenia. Ta metoda przyjmuje jeden z ciągów formatowania wyliczenia, aby określić wartość, która ma zostać zwrócona.

W poniższych sekcjach wymieniono ciągi formatowania wyliczenia i zwracane przez nie wartości. W tych specyfikatorach formatu nie jest rozróżniana wielkość liter.

## <a name="g-or-g"></a>G lub g

Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe, i w przeciwnym razie wyświetla wartość całkowitą bieżącego wystąpienia. Jeśli Wyliczenie jest zdefiniowane przy użyciu ustawionych atrybutów **flag** , wartości ciągów każdego poprawnego wpisu są łączone razem, oddzielone przecinkami. Jeśli atrybut **flags** nie jest ustawiony, nieprawidłowa wartość jest wyświetlana jako wpis liczbowy. Poniższy przykład ilustruje specyfikator formatu G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F lub f

Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe. Jeśli wartość może być w pełni wyświetlana jako suma wpisów w wyliczeniu (nawet jeśli nie ma atrybutu **flags** ), wartości ciągu każdego z prawidłowych wpisów są połączone, oddzielone przecinkami. Jeśli wartość nie może być całkowicie określona przez wpisy wyliczenia, wartość jest formatowana jako wartość całkowita. Poniższy przykład ilustruje specyfikator formatu F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D lub d

Wyświetla wpis wyliczenia jako wartość całkowitą w najkrótszej możliwej reprezentacji. Poniższy przykład ilustruje specyfikator formatu D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X lub x

Wyświetla wpis wyliczenia jako wartość szesnastkową. Wartość jest reprezentowana z wiodącymi zerami w razie potrzeby, aby upewnić się, że ciąg wynikowy ma dwa znaki dla każdego bajtu w [podstawowym typie liczbowym](xref:System.Enum.GetUnderlyingType%2A)typu wyliczenia. Poniższy przykład ilustruje specyfikator formatu X. W przykładzie typ podstawowy obu <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> jest <xref:System.Int32> lub 32-bitową (lub 4-bajtową) liczbę całkowitą, która tworzy 8-znakowy ciąg wynikowy.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano Wyliczenie `Colors` , które składa się z trzech wpisów: `Red` , `Blue` , i `Green` .

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Po zdefiniowaniu wyliczenia wystąpienie może być deklarowane w następujący sposób.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

`Color.ToString(System.String)`Metoda może następnie służyć do wyświetlania wartości wyliczenia na różne sposoby, w zależności od przenoszonego specyfikatora formatu.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Zobacz też

- [Formatowanie typów](formatting-types.md)
