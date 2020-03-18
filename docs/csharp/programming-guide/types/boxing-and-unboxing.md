---
title: Boks i unboxing - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745414"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)

Boks jest procesem konwertowania [typu](../../language-reference/builtin-types/value-types.md) wartości `object` na typ lub dowolny typ interfejsu zaimplementowany przez ten typ wartości. Gdy program CLR (Common Language runtime) zawiera wartość, zawija wartość wewnątrz <xref:System.Object?displayProperty=nameWithType> wystąpienia i przechowuje ją na zarządzanym stosie. Rozpakowywanie wyodrębnia typ wartości z obiektu. Boks jest niejawny; unboxing jest jawny. Pojęcie boksu i rozpakowywania leży u podstaw zunifikowanego widoku c# systemu typów, w którym wartość dowolnego typu może być traktowana jako obiekt.

W poniższym przykładzie zmienna `i` całkowita jest *zapakowana* i przypisana do obiektu `o`.

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

Obiekt `o` można następnie rozpakować i przypisać do `i`zmiennej całkowitej:

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Poniższe przykłady ilustrują sposób, w jaki boks jest używany w języku C#.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Wydajność

W odniesieniu do prostych zadań, boks i rozpakowywanie są obliczeniowo kosztownymi procesami. Gdy typ wartości jest zapakowany, nowy obiekt musi zostać przydzielony i skonstruowany. W mniejszym stopniu, oddanych wymaganych do unboxing jest również drogie obliczeniowo. Aby uzyskać więcej informacji, zobacz [Wydajność](../../../framework/performance/performance-tips.md).

## <a name="boxing"></a>Boxing

Boks służy do przechowywania typów wartości w stercie zebrane jut. Boks jest niejawną konwersją typu `object` [wartości](../../language-reference/builtin-types/value-types.md) na typ lub dowolny typ interfejsu zaimplementowany przez ten typ wartości. Boksuje typ wartości przydziela wystąpienie obiektu na stercie i kopiuje wartość do nowego obiektu.

Należy wziąć pod uwagę następującą deklarację zmiennej typu wartości:

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

Następująca instrukcja niejawnie stosuje operację bokserską na zmiennej: `i`

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Wynikiem tej instrukcji jest tworzenie `o`odwołania do obiektu , na stosie, który odwołuje się do wartości typu `int`, na stercie. Ta wartość jest kopią wartości typu przypisanej `i`do zmiennej . Różnica między dwiema `i` zmiennymi, i `o`, jest zilustrowana na poniższym obrazie konwersji bokserskiej:

![Grafika pokazująca różnicę między zmiennymi i i i o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Możliwe jest również jawnie wykonywanie boksu, jak w poniższym przykładzie, ale jawne boks nigdy nie jest wymagane:

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Opis

W tym przykładzie konwertuje zmienną `i` całkowitą na obiekt `o` przy użyciu boksu. Następnie wartość przechowywana w `i` zmiennej `123` `456`zostanie zmieniona z na . W przykładzie pokazano, że oryginalny typ wartości i obiekt w pudełku używają oddzielnych lokalizacji pamięci i dlatego mogą przechowywać różne wartości.

## <a name="example"></a>Przykład

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Unboxing

Unboxing jest jawną konwersją z typu `object` na typ [wartości](../../language-reference/builtin-types/value-types.md) lub z typu interfejsu do typu wartości, który implementuje interfejs. Operacja rozpakowywania składa się z:

- Sprawdzanie wystąpienia obiektu, aby upewnić się, że jest to wartość zapakowana danego typu wartości.

- Kopiowanie wartości z wystąpienia do zmiennej typu wartości.

Następujące instrukcje pokazują operacje bokserskie i rozpakowywania:

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

Na poniższym rysunku przedstawiono wynik poprzednich instrukcji:

![Grafika przedstawiająca konwersję rozpakowywania.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Dla rozpakowywania typów wartości, aby odnieść sukces w czasie wykonywania, element jest unboxed musi być odwołanie do obiektu, który został wcześniej utworzony przez bokserskie wystąpienie tego typu wartości. Próba rozpakowywania `null` <xref:System.NullReferenceException>powoduje . Próba odpakowania odwołania do niezgodnego typu <xref:System.InvalidCastException>wartości powoduje , że .

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono przypadek nieprawidłowego unboxing `InvalidCastException`i wynikowy . Po `try` `catch`wystąpieniu błędu wyświetlany jest komunikat o błędzie i o błędzie.

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

Ten program wyprowadza:

`Specified cast is not valid. Error: Incorrect unboxing.`

Jeśli zmienisz instrukcję:

```csharp
int j = (short) o;
```

na:

```csharp
int j = (int) o;
```

konwersja zostanie wykonana, a otrzymasz dane wyjściowe:

`Unboxing OK.`

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
- [Typy wartości](../../language-reference/builtin-types/value-types.md)
