---
title: Odbicie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: f47f78ff9989fc44ad46b66a447061c3fa84a86e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reflection-visual-basic"></a>Odbicie (Visual Basic)
Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawy, moduły i typy. Odbicie umożliwia dynamicznie utworzyć wystąpienia typu, powiązać danego typu do istniejącego obiektu, lub pobranie typu z istniejącego obiektu i wywołanie metody lub dostępu do swoich pól i właściwości. Jeśli używane są atrybuty w kodzie, odbicia umożliwia dostęp do nich. Aby uzyskać więcej informacji, zobacz [atrybutów](../../../standard/attributes/index.md).  
  
 Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowa klasa — można uzyskać typu zmienną:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Wynik jest:  
  
 `System.Int32`  
  
 W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowanego zestawu.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Wynik jest:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Odbicie — omówienie  
 Odbicie jest przydatne w następujących sytuacjach:  
  
-   Jeśli użytkownik ma dostęp do atrybutów w metadanych programu. Aby uzyskać więcej informacji, zobacz [pobierania informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
-   Badanie i tworzenie wystąpień typów w zestawie.  
  
-   Do tworzenia nowych typów w czasie wykonywania. Korzystanie z klas w <xref:System.Reflection.Emit>.  
  
-   Do wykonania późne wiązanie podczas uzyskiwania dostępu do metody na typach utworzone w czasie wykonywania. Zobacz temat [dynamiczne ładowanie i przy użyciu typów](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Odbicie](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [Wyświetlanie informacji o typie](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [Odbicie i typy ogólne](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Pobieranie informacji przechowywanych w atrybutach](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku Visual Basic](../../../visual-basic/programming-guide/index.md)  
 [Zestawy w środowisku uruchomieniowym CLR](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
