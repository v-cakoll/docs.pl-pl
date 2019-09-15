---
title: OdbicieC#()
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 7906ca6f02a369e6f4d51f11f96616b6a89f48c5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971661"
---
# <a name="reflection-c"></a>OdbicieC#()
Odbicie zawiera obiekty (typu <xref:System.Type>) opisujące zestawy, moduły i typy. Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości. Jeśli używasz atrybutów w kodzie, odbicie umożliwia uzyskanie dostępu do nich. Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).  
  
 Oto prosty przykład odbicia przy użyciu metody `GetType` statycznej dziedziczonej przez wszystkie typy `Object` z klasy podstawowej — w celu uzyskania typu zmiennej:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Dane wyjściowe:  
  
 `System.Int32`  
  
 Poniższy przykład używa odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Dane wyjściowe:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> C# Słowa kluczowe `protected` i`internal` nie mają znaczenia w Il i nie są używane w interfejsach API odbicia. Odpowiednie warunki w IL są *rodziną* i *zestawem*. Aby zidentyfikować `internal` metodę przy użyciu odbicia, <xref:System.Reflection.MethodBase.IsAssembly%2A> należy użyć właściwości. Aby zidentyfikować `protected internal` metodę, <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>Użyj.  
  
## <a name="reflection-overview"></a>Przegląd odbicia  
 Odbicie jest przydatne w następujących sytuacjach:  
  
- Gdy musisz uzyskać dostęp do atrybutów w metadanych programu. Aby uzyskać więcej informacji, zobacz artykuł [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Do badania i tworzenia wystąpień typów w zestawie.  
  
- Do kompilowania nowych typów w czasie wykonywania. Użyj klas w <xref:System.Reflection.Emit>.  
  
- Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod w typach utworzonych w czasie wykonywania. Zobacz temat [dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Wyświetlanie informacji o typie](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
