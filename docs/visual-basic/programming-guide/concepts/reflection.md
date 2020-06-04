---
title: Odbicie
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 43c05a0b3bbfc3dfc304b1aed3f689625a40229a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413183"
---
# <a name="reflection-visual-basic"></a>Odbicie (Visual Basic)
Odbicie zawiera obiekty (typu <xref:System.Type> ) opisujące zestawy, moduły i typy. Możesz użyć odbicia, aby dynamicznie utworzyć wystąpienie typu, powiązać typ z istniejącym obiektem lub uzyskać typ z istniejącego obiektu i wywołać jego metody lub uzyskać dostęp do jego pól i właściwości. Jeśli używasz atrybutów w kodzie, odbicie umożliwia uzyskanie dostępu do nich. Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).  
  
 Oto prosty przykład odbicia przy użyciu metody statycznej `GetType` dziedziczonej przez wszystkie typy z `Object` klasy podstawowej — w celu uzyskania typu zmiennej:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Dane wyjściowe wyglądają następująco:  
  
 `System.Int32`  
  
 Poniższy przykład używa odbicia w celu uzyskania pełnej nazwy załadowanego zestawu.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Dane wyjściowe wyglądają następująco:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Przegląd odbicia  
 Odbicie jest przydatne w następujących sytuacjach:  
  
- Gdy musisz uzyskać dostęp do atrybutów w metadanych programu. Aby uzyskać więcej informacji, zobacz artykuł [pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Do badania i tworzenia wystąpień typów w zestawie.  
  
- Do kompilowania nowych typów w czasie wykonywania. Użyj klas w <xref:System.Reflection.Emit> .  
  
- Do wykonywania późnego wiązania, uzyskiwanie dostępu do metod w typach utworzonych w czasie wykonywania. Zobacz temat [dynamiczne ładowanie i używanie typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Więcej informacji:  
  
- [Odbicie](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Wyświetlanie informacji o typie](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w Visual Basic](../index.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
