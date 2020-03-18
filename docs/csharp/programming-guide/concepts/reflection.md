---
title: Odbicie (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711662"
---
# <a name="reflection-c"></a>Odbicie (C#)

Odbicie zapewnia obiekty <xref:System.Type>(typu), które opisują zespoły, moduły i typy. Odbicie można użyć do dynamicznego utworzenia wystąpienia typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości. Jeśli używasz atrybutów w kodzie, odbicie umożliwia dostęp do nich. Aby uzyskać więcej informacji, zobacz [Atrybuty](../../../standard/attributes/index.md).

Oto prosty przykład odbicia przy <xref:System.Object.GetType> użyciu metody - dziedziczone `Object` przez wszystkie typy z klasy podstawowej - w celu uzyskania typu zmiennej:

> [!NOTE]
> Upewnij się, `using System;` `using System.Reflection;` że dodajesz i jesteś na górze pliku *.cs.*

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Wyjście to: `System.Int32`.

W poniższym przykładzie użyto odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Wyjście to: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> C# słowa `protected` kluczowe `internal` i nie mają znaczenia w IL i nie są używane w interfejsach API odbicia. Odpowiednie terminy w IL to *Rodzina* i *Montaż.* Aby zidentyfikować `internal` metodę przy <xref:System.Reflection.MethodBase.IsAssembly%2A> użyciu odbicia, należy użyć właściwości. Aby zidentyfikować `protected internal` metodę, <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>należy użyć pliku .

## <a name="reflection-overview"></a>Przegląd refleksji

Odbicie jest przydatne w następujących sytuacjach:

- Gdy trzeba uzyskać dostęp do atrybutów w metadanych programu. Aby uzyskać więcej informacji, zobacz [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Do badania i tworzenia wystąpień typów w zestawie.
- Do tworzenia nowych typów w czasie wykonywania. Użyj klas <xref:System.Reflection.Emit>w .
- Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod na typy utworzone w czasie wykonywania. Zobacz temat [Dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).

## <a name="related-sections"></a>Sekcje pokrewne

Więcej informacji:

- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)
- [Wyświetlanie informacji o typie](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
