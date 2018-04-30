---
title: 'Porady: ładowanie zestawów do kontekstu Reflection-Only'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ab0224dd0452003f1d43a314d03aaca0fe04fda
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Porady: ładowanie zestawów do kontekstu Reflection-Only
Kontekstu ładowania tylko odbicie można zbadać zestawy skompilowany dla innych platform lub innych wersji programu .NET Framework. Tylko można zbadać kodu załadowanego w tym kontekście; Nie można wykonać. Oznacza to, że nie można utworzyć obiektów, ponieważ nie można wykonać konstruktorów. Ponieważ nie można wykonać kod, zależności nie są ładowane automatycznie. Jeśli potrzebujesz zbadać je, należy załadować je samodzielnie.  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Aby załadować zestawu do kontekstu ładowania tylko odbicie  
  
1.  Użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> przeciążenie metody można załadować zestawu podanej nazwy wyświetlanej, lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody można załadować zestawu podanej ścieżki. Jeśli zestaw jest obraz binarny, użyj <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> przeciążenie metody.  
  
    > [!NOTE]
    >  Za pomocą kontekstu reflection-only nie można załadować wersji biblioteki mscorlib.dll z wersji programu .NET Framework innej niż wersja w kontekstu wykonywania.  
  
2.  Jeśli zestaw zawiera zależności, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> — metoda nie załadować je. Jeśli potrzebujesz zbadać je, należy załadować je samodzielnie.  
  
3.  Określić, czy zestaw jest ładowany do kontekstu reflection-only przy użyciu zestawu <xref:System.Reflection.Assembly.ReflectionOnly%2A> właściwości.  
  
4.  Jeśli atrybuty zostały zastosowane do zestawu lub typów w zestawie, Sprawdź te atrybuty przy użyciu <xref:System.Reflection.CustomAttributeData> klasy, aby upewnić się, że nie są podejmowane próby wykonania kodu w kontekstu reflection-only. Użyj odpowiedniego przeciążenia <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Reflection.CustomAttributeData> obiektów reprezentujących atrybuty stosowane do zestawu, elementu członkowskiego, modułu lub parametr.  
  
    > [!NOTE]
    >  Atrybuty stosowane do zestawu lub jego zawartość może być zdefiniowana w zestawie lub może być zdefiniowana w innym zestawie ładowane do kontekstu reflection-only. Nie istnieje sposób mówić z wyprzedzeniem, gdzie są zdefiniowane atrybuty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak zbadać atrybutów zastosowany do zestawu ładowane do kontekstu reflection-only.  
  
 Przykładowy kod definiuje atrybut niestandardowy dwa konstruktory i jedną właściwość. Atrybut jest stosowany do zestawu, na typ zadeklarowany w zestawie, metody typu i parametru metody. Po wykonaniu zestaw ładuje się do kontekstu reflection-only i wyświetla informacje o niestandardowych atrybutów, które zostały zastosowane oraz typy i składniki, które zawiera.  
  
> [!NOTE]
>  Aby uprościć przykładów kodu, zestaw ładuje i sprawdza sama. Zwykle nie będzie Oczekiwano znalezienia tego samego zestawu ładowane do zarówno kontekstu wykonywania i kontekstu reflection-only.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>  
 <xref:System.Reflection.CustomAttributeData>
