---
title: OdbicieC#()
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711662"
---
# <a name="reflection-c"></a>OdbicieC#()

Odbicie udostępnia obiekty (typu <xref:System.Type>) opisujące zestawy, moduły i typy. Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości. Jeśli używasz atrybutów w kodzie, odbicie umożliwia uzyskanie dostępu do nich. Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).

Oto prosty przykład odbicia przy użyciu metody <xref:System.Object.GetType> dziedziczonej przez wszystkie typy z klasy podstawowej `Object` — Aby uzyskać typ zmiennej:

> [!NOTE]
> Upewnij się, że dodano `using System;` i `using System.Reflection;` w górnej części pliku *. cs* .

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Dane wyjściowe to: `System.Int32`.

Poniższy przykład używa odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Dane wyjściowe to: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> C# Słowa kluczowe `protected` i `internal` nie mają znaczenia w Il i nie są używane w interfejsach API odbicia. Odpowiednie warunki w IL są *rodziną* i *zestawem*. Aby zidentyfikować metodę `internal` przy użyciu odbicia, należy użyć właściwości <xref:System.Reflection.MethodBase.IsAssembly%2A>. Aby zidentyfikować metodę `protected internal`, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

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
