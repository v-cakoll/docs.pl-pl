---
title: "Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18e580a67d5a983d61ab3c0b71cfc7d294468010
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
Przekazywanie dalej typu umożliwia przeniesienie typu do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.  
  
 Na przykład, załóżmy, że aplikacja używa `Example` klasa w zestawie o nazwie `Utility.dll`. Deweloperzy `Utility.dll` zdecydować o Refaktoryzuj zestawu, a w procesie może przenieść `Example` klasy do innego zestawu. Jeśli stara wersja `Utility.dll` zostało zastąpione przez nową wersję `Utility.dll` i jego zestawu uzupełniających, aplikacji używającej `Example` klasy nie powiedzie się, ponieważ nie można zlokalizować `Example` klasy w nowej wersji `Utility.dll`.  
  
 Deweloperzy `Utility.dll` można tego uniknąć przekazywania żądań `Example` przy użyciu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atrybutu. Jeśli zastosowano atrybut do nowej wersji `Utility.dll`, żądania dotyczące `Example` klasy są przekazywane do zestawu, który zawiera teraz klasy. Istniejącej aplikacji działa normalnie, bez ponownej kompilacji.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 2.0 nie można przesłać dalej typy z zestawów napisane w języku Visual Basic. Jednak aplikacja napisana w języku Visual Basic, jaką może wykorzystać typów przekazywane. Oznacza to jeśli aplikacja używa zestawu kodowane w języku C# lub języka C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacji Visual Basic można użyć typu przekazany dalej.  
  
## <a name="forwarding-types"></a>Przekazywanie typów  
 Istnieją cztery kroki do przesyłania dalej typu:  
  
1.  Przenoszenie kodu źródłowego dla typu z oryginalnego zestawu do zestawu docelowego.  
  
2.  W zestawie, gdzie typ używany do można znaleźć, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, która została przeniesiona. Poniższy kod przedstawia atrybut typu o nazwie `Example` który został przeniesiony.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Kompilowanie zestawu, który zawiera teraz typu.  
  
4.  Skompiluj ponownie zestawu, gdzie typ używany do znajdować się odwołanie do zestawu, który zawiera teraz typ. Na przykład, jeśli kompilacja pliku C# z wiersza polecenia, użyj [/Reference (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) opcję, aby określić zestaw zawierający typ. W języku C++ użyj [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) dyrektywy w pliku źródłowym, aby określić zestaw zawierający typ.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [Przekazywanie dalej typu (C + +/ CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [#using — dyrektywa](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
