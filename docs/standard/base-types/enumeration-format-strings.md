---
title: Ciągi formatu wyliczenia
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
ms.openlocfilehash: da7634758f5c4319fa18612d216682dc141318fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155961"
---
# <a name="enumeration-format-strings"></a>Ciągi formatu wyliczenia

<xref:System.Enum.ToString%2A?displayProperty=nameWithType> Metoda służy do tworzenia nowego obiektu ciągu, który reprezentuje wartość liczbową, szesnastkową lub ciągową elementu członkowskiego wyliczenia. Ta metoda przyjmuje jeden z ciągów formatowania wyliczenia, aby określić wartość, która ma zostać zwrócona.

W poniższych sekcjach wymieniono ciągi formatowania wyliczenia i zwracane przez nie wartości. Te specyfikatory formatu nie są uwzględniane wielkości liter.

## <a name="g-or-g"></a>G lub g

Wyświetla wpis wyliczenia jako wartość ciągu, jeśli to możliwe, i w inny sposób wyświetla wartość całkowitą bieżącego wystąpienia. Jeśli wyliczenie jest zdefiniowane z **zestawem atrybutów Flags,** wartości ciągu każdego prawidłowego wpisu są ze sobą łączone, oddzielone przecinkami. Jeśli atrybut **Flagi** nie jest ustawiony, jako wpis liczbowy jest wyświetlana nieprawidłowa wartość. W poniższym przykładzie przedstawiono specyfikator formatu G.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F lub f

Wyświetla wpis wyliczenia jako wartość ciągu, jeśli to możliwe. Jeśli wartość może być całkowicie wyświetlana jako podsumowanie wpisów w wyliczeniu (nawet jeśli atrybut **Flags** nie jest obecny), wartości ciągu każdego prawidłowego wpisu są łączone ze sobą, oddzielone przecinkami. Jeśli wartość nie może być całkowicie określona przez wpisy wyliczenia, wartość jest formatowana jako wartość całkowita. W poniższym przykładzie przedstawiono specyfikator formatu F.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D lub d

Wyświetla wpis wyliczenia jako wartość całkowitą w najkrótszej możliwej reprezentacji. W poniższym przykładzie przedstawiono specyfikator formatu D.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X lub x

Wyświetla wpis wyliczenia jako wartość szesnastkowa. Wartość jest reprezentowana z zerami wiodącymi, w razie potrzeby, aby upewnić się, że ciąg wynikowy ma dwa znaki dla każdego bajtu w [typie liczbowym](xref:System.Enum.GetUnderlyingType%2A)typu wyliczenia. W poniższym przykładzie przedstawiono specyfikator formatu X. W przykładzie podstawowym typem obu <xref:System.ConsoleColor> <xref:System.IO.FileAttributes> i <xref:System.Int32>jest , lub 32-bitowa (lub 4-bajtowa) liczba całkowita, która tworzy 8-znakowy ciąg wyniku.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano `Colors` wyliczenie o `Red` `Blue`nazwie, `Green`która składa się z trzech wpisów: , , i .

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Po zdefiniowaniu wyliczenia wystąpienie można zadeklarować w następujący sposób.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

Metoda `Color.ToString(System.String)` może być następnie używana do wyświetlania wartości wyliczenia na różne sposoby, w zależności od specyfikatora formatu przekazanego do niej.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Zobacz też

- [Formatowanie typów](formatting-types.md)
