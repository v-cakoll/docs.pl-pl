---
title: 'Porady: ładowanie zestawów do kontekstu Reflection-Only'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
ms.openlocfilehash: cac6b3b3adf070ad6070e5c5941653f20dedd907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130103"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Porady: ładowanie zestawów do kontekstu Reflection-Only

Kontekst ładowania tylko odbicie umożliwia badanie zestawów skompilowanych dla innych platform lub dla innych wersji .NET Framework. Kod załadowany do tego kontekstu może być badany tylko; nie można go wykonać. Oznacza to, że nie można tworzyć obiektów, ponieważ nie można wykonać konstruktorów. Ponieważ kod nie może zostać wykonany, zależności nie są ładowane automatycznie. Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Aby załadować zestaw do kontekstu ładowania tylko odbicie

1. Użyj przeciążenia <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> metody, aby załadować zestaw przy użyciu jego nazwy wyświetlanej, lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodę ładowania zestawu przy użyciu jej ścieżki. Jeśli zestaw jest obrazem binarnym, Użyj przeciążenia <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> metody.

    > [!NOTE]
    > Nie można użyć kontekstu tylko odbicia do załadowania wersji biblioteki mscorlib. dll z wersji .NET Framework innej niż wersja w kontekście wykonania.

2. Jeśli zestaw ma zależności, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Metoda nie ładuje ich. Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.

3. Ustal, czy zestaw jest ładowany do kontekstu tylko odbicie przy użyciu <xref:System.Reflection.Assembly.ReflectionOnly%2A> właściwości zestawu.

4. Jeśli atrybuty zostały zastosowane do zestawu lub do typów w zestawie, sprawdź te atrybuty przy użyciu <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie podjęto próby wykonania kodu w kontekście "tylko odbicie". Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody w celu uzyskania <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty zastosowane do zestawu, elementu członkowskiego, modułu lub parametru.

    > [!NOTE]
    > Atrybuty zastosowane do zestawu lub jego zawartości mogą być zdefiniowane w zestawie lub mogą być zdefiniowane w innym zestawie załadowanym do kontekstu tylko odbicie. Nie ma możliwości poinformowania z wyprzedzeniem o zdefiniowaniu atrybutów.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak sprawdzać atrybuty zastosowane do zestawu załadowanego do kontekstu tylko odbicie.

Przykładowy kod definiuje atrybut niestandardowy z dwoma konstruktorami i jedną właściwością. Ten atrybut jest stosowany do zestawu, do typu zadeklarowanego w zestawie, do metody typu i do parametru metody. Po wykonaniu zestaw ładuje się do kontekstu tylko odbicia i wyświetla informacje o niestandardowych atrybutach, które zostały zastosowane do niego, oraz do typów i składowych, które zawiera.

> [!NOTE]
> Aby uprościć przykład kodu, zestaw ładuje i sprawdza siebie. Zwykle nie oczekuje się, że ten sam zestaw został załadowany do zarówno kontekstu wykonywania, jak i kontekstu tylko odbicie.

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
