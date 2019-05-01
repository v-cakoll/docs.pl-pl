---
title: Odbicie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: d2ad8957d308aa98935c862ec1864b6682be904b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783529"
---
# <a name="reflection-visual-basic"></a>Odbicie (Visual Basic)
Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawów, modułów i typów. Można używać odbicia do dynamicznego utworzenia wystąpienia typu, powiązania typu z istniejącym obiektem lub uzyskania typu z istniejącego obiektu i wywoływania jego metody lub dostępu do jego pola i właściwości. Jeśli używasz atrybutów w kodzie, odbicie umożliwia dostęp do nich. Aby uzyskać więcej informacji, zobacz [atrybuty](../../../standard/attributes/index.md).  
  
 Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowej klasy — w celu uzyskania typu zmiennej:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Dane wyjściowe to:  
  
 `System.Int32`  
  
 W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowany zestaw.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Dane wyjściowe to:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
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

- [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)
- [Zestawy w środowisku uruchomieniowym CLR](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
