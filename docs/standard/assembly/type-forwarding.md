---
title: Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
description: Przekazywanie typu pozwala przenieść typ do innego zestawu platformy .NET bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f0be61bd4ce88569e22a350a9ea9490d67e74ff3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378594"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
Przekazywanie typu pozwala przenieść typ do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.  
  
 Załóżmy na przykład, że aplikacja używa `Example` klasy w zestawie o nazwie *Utility. dll*. Deweloperzy *Narzędzia Utility. dll* mogą zdecydować się na refaktoryzację zestawu, a w procesie może przenieść `Example` klasę do innego zestawu. Jeśli stara wersja *Narzędzia Utility. dll* jest zastępowana przez nową wersję *pliku Utility. dll* i jego zestawu towarzyszącego, aplikacja, która używa `Example` klasy, kończy się niepowodzeniem, ponieważ nie może zlokalizować `Example` klasy w nowej wersji *pliku Utility. dll*.  
  
 Deweloperzy *Narzędzia Utility. dll* mogą uniknąć tego przez przekazywanie żądań dla `Example` klasy przy użyciu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atrybutu. Jeśli atrybut został zastosowany do nowej wersji *pliku Utility. dll*, żądania dla `Example` klasy są przekazywane do zestawu, który zawiera teraz klasę. Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 nie można przesłać dalej typów z zestawów utworzonych w Visual Basic. Jednak aplikacja zapisywana w Visual Basic może korzystać z przekazanych typów. Oznacza to, że jeśli aplikacja używa zestawu kodowanego w języku C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może użyć przekazanego typu.  
  
## <a name="forward-types"></a>Typy do przodu  
 Aby przesłać dalej typ, należy wykonać cztery kroki:  
  
1. Przenieś kod źródłowy dla typu z oryginalnego zestawu do zestawu docelowego.  

2. W zestawie, w którym używany jest typ, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, który został przeniesiony. Poniższy kod przedstawia atrybut dla typu o nazwie `Example` , który został przeniesiony.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Kompiluj zestaw, który zawiera teraz typ.  

4. Ponownie skompiluj zestaw, w którym znajduje się typ, z odwołaniem do zestawu, który zawiera teraz typ. Na przykład, Jeśli kompilujesz plik C# z wiersza polecenia, użyj opcji [-Reference (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) , aby określić zestaw, który zawiera typ. W języku C++ Użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Przekazywanie dalej typu (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using — dyrektywa](/cpp/preprocessor/hash-using-directive-cpp)
