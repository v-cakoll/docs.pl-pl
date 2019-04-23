---
title: 'Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dc05d27b0316c82c5314a766fcad929dc5f3698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976745"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Instrukcje: Ładowanie zestawów do kontekstu Reflection-Only
Kontekst ładowania tylko odbicie umożliwia analizowanie zestawy skompilowane dla innych platform lub w przypadku innych wersji systemu .NET Framework. Tylko można zbadać kodu załadowanego w tym kontekście; Nie można wykonać. Oznacza to, że nie można utworzyć obiektów, ponieważ nie można wykonać konstruktorów. Ponieważ nie można wykonać kod, zależności nie są ładowane automatycznie. Jeśli musisz zbadać je, należy załadować je samodzielnie.  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Ładowanie zestawów do kontekstu ładowania tylko odbicie  
  
1. Użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> przeciążenia metody, aby załadować zestawu, biorąc pod uwagę jego nazwę wyświetlaną lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodę, aby załadować zestaw podanej ścieżce. Jeśli zestaw jest obrazem binarnym, użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> przeciążenie metody.  
  
    > [!NOTE]
    >  Za pomocą kontekstu reflection-only nie można załadować wersji biblioteki mscorlib.dll z wersji programu .NET Framework niż wersja w kontekście wykonywania.  
  
2. Jeśli zestaw ma zależności, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> metoda nie ładuje je. Jeśli musisz zbadać je, należy załadować je samodzielnie.  
  
3. Ustal, czy zestaw jest ładowany do kontekstu reflection-only przy użyciu zestawu <xref:System.Reflection.Assembly.ReflectionOnly%2A> właściwości.  
  
4. Jeśli atrybuty zostały zastosowane do zestawu lub typów w zestawie, należy zbadać te atrybuty, używając <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie są podejmowane próby wykonania kodu w kontekstu reflection-only. Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty stosowane do zestawu, elementu członkowskiego, modułu lub parametr.  
  
    > [!NOTE]
    >  Atrybuty stosowane do zestawu lub jego zawartość może być zdefiniowane w zestawie lub może być zdefiniowana w innym zestawie ładowane do kontekstu reflection-only. Nie ma możliwości z wyprzedzeniem sprawdzić, gdzie są zdefiniowane atrybuty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje jak zbadać atrybuty stosowane do zestawu ładowane do kontekstu reflection-only.  
  
 Przykładowy kod definiuje dwa konstruktory i jedną właściwość atrybutu niestandardowego. Ten atrybut jest stosowany do zestawu, do typu zadeklarowany w zestawie, do metody typu i parametru metody. Po wykonaniu zestawu ładuje się do kontekstu reflection-only i wyświetla informacje na temat atrybutów niestandardowych, które zostały zastosowane do niego i typy i elementy członkowskie, które zawiera.  
  
> [!NOTE]
>  Aby uprościć przykład kodu, zestaw ładuje i sprawdza się. Zwykle będzie spodziewa się znaleźć tego samego zestawu, które są ładowane do kontekstu wykonywania i kontekstu reflection-only.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
