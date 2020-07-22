---
title: 'Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only'
description: Zapoznaj się z przykładem ładowania zestawów do kontekstu tylko odbicie w programie .NET. Należy zapoznać się z zestawami skompilowanymi dla innych platform lub wersji platformy .NET.
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
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865076"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only

Kontekst ładowania tylko odbicie umożliwia badanie zestawów skompilowanych dla innych platform lub dla innych wersji .NET Framework. Kod załadowany do tego kontekstu może być badany tylko; nie można go wykonać. Oznacza to, że nie można tworzyć obiektów, ponieważ nie można wykonać konstruktorów. Ponieważ kod nie może zostać wykonany, zależności nie są ładowane automatycznie. Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Aby załadować zestaw do kontekstu ładowania tylko odbicie

1. Użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> przeciążenia metody, aby załadować zestaw przy użyciu jego nazwy wyświetlanej, lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodę ładowania zestawu przy użyciu jej ścieżki. Jeśli zestaw jest obrazem binarnym, użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> przeciążenia metody.

    > [!NOTE]
    > Nie można użyć kontekstu tylko odbicia do załadowania wersji mscorlib.dll z wersji .NET Framework innej niż wersja w kontekście wykonania.

2. Jeśli zestaw ma zależności, metoda nie <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ładuje ich. Jeśli musisz je przeanalizować, musisz załadować je samodzielnie.

3. Ustal, czy zestaw jest ładowany do kontekstu tylko odbicie przy użyciu <xref:System.Reflection.Assembly.ReflectionOnly%2A> Właściwości zestawu.

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
