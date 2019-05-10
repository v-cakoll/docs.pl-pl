---
title: Odbicie (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 4593aeef13f5d1d0c223b40e266556cb2bcfee5f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595551"
---
# <a name="reflection-c"></a>Odbicie (C#)
Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawów, modułów i typów. Można używać odbicia do dynamicznego utworzenia wystąpienia typu, powiązania typu z istniejącym obiektem lub uzyskania typu z istniejącego obiektu i wywoływania jego metody lub dostępu do jego pola i właściwości. Jeśli używasz atrybutów w kodzie, odbicie umożliwia dostęp do nich. Aby uzyskać więcej informacji, zobacz [atrybuty](../../../../docs/standard/attributes/index.md).  
  
 Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowej klasy — w celu uzyskania typu zmiennej:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Dane wyjściowe to:  
  
 `System.Int32`  
  
 W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowany zestaw.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Dane wyjściowe to:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  Słowa kluczowe języka C# `protected` i `internal` nie mają znaczenia IL i nie są używane w odbiciu interfejsów API. Odpowiednie postanowienia IL są *rodziny* i *zestawu*. Aby zidentyfikować `internal` przy użyciu odbicia, użyj metody <xref:System.Reflection.MethodBase.IsAssembly%2A> właściwości. Aby zidentyfikować `protected internal` metody, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## <a name="reflection-overview"></a>Omówienie odbicia  
 Odbicie jest przydatne w następujących sytuacjach:  
  
- Jeśli masz dostęp do atrybutów w metadanych programu. Aby uzyskać więcej informacji, zobacz [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Badanie i tworzenie wystąpień typów w zestawie.  
  
- Do tworzenia nowych typów w czasie wykonywania. Używanie klas w <xref:System.Reflection.Emit>.  
  
- Do wykonywania późne powiązania, uzyskiwanie dostępu do metody na typach tworzony w czasie wykonywania. Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Wyświetlanie informacji o typie](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zestawy w środowisku uruchomieniowym CLR](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
