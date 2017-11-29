---
title: Odbicie (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f567eb47d93fcd95e5895b4b44e1c89fb0b901b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-c"></a>Odbicie (C#)
Odbicie udostępnia obiekty (typu <xref:System.Type>) opisują zestawy, moduły i typy. Odbicie umożliwia dynamicznie utworzyć wystąpienia typu, powiązać danego typu do istniejącego obiektu, lub pobranie typu z istniejącego obiektu i wywołanie metody lub dostępu do swoich pól i właściwości. Jeśli używane są atrybuty w kodzie, odbicia umożliwia dostęp do nich. Aby uzyskać więcej informacji, zobacz [atrybutów](https://msdn.microsoft.com/library/5x6cd29c).  
  
 Poniżej przedstawiono prosty przykład odbicia przy użyciu metody statycznej `GetType` — dziedziczone przez wszystkie typy z `Object` podstawowa klasa — można uzyskać typu zmienną:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 Wynik jest:  
  
 `System.Int32`  
  
 W poniższym przykładzie użyto odbicia, aby uzyskać pełną nazwę załadowanego zestawu.  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 Wynik jest:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  Słowa kluczowe języka C# `protected` i `internal` mają znaczenia w IL i nie są używane w odbicia interfejsów API. Odpowiednie warunki IL *rodziny* i *zestawu*. Aby zidentyfikować `internal` za pomocą odbicia, użyj metody <xref:System.Reflection.MethodBase.IsAssembly%2A> właściwości. Aby zidentyfikować `protected internal` metody, użyj <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
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
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zestawy w środowisko uruchomieniowe języka wspólnego](https://msdn.microsoft.com/library/k3677y81)
