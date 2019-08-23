---
title: Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1b05a5548beb7e7c1f0ec8e96b6e02350318ef9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921420"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
Przekazywanie typu pozwala przenieść typ do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.  
  
 Załóżmy na przykład, że aplikacja używa `Example` klasy w zestawie o nazwie. `Utility.dll` Deweloperzy `Utility.dll` mogą zdecydować się na refaktoryzację zestawu, a w procesie może `Example` przenieść klasę do innego zestawu. Jeśli stara `Utility.dll` wersja programu jest zastępowana przez nową wersję programu `Utility.dll` i jego zestaw towarzyszący, aplikacja, która używa `Example` klasy, kończy się niepowodzeniem, ponieważ `Example` nie może zlokalizować klasy w nowej `Utility.dll`wersji programu.  
  
 Deweloperzy `Utility.dll` mogą uniknąć tego przez przekazywanie żądań `Example` dla klasy przy użyciu <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atrybutu. Jeśli atrybut został zastosowany do nowej wersji programu `Utility.dll`, żądania `Example` dla klasy są przekazywane do zestawu, który teraz zawiera klasę. Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 nie można przesłać dalej typów z zestawów utworzonych w Visual Basic. Jednak aplikacja zapisywana w Visual Basic może korzystać z przekazanych typów. Oznacza to, że jeśli aplikacja używa zestawu zakodowanego w C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może użyć przekazanego typu.  
  
## <a name="forwarding-types"></a>Typy przekazywania  
 Aby przesłać dalej typ, należy wykonać cztery kroki:  
  
1. Przenieś kod źródłowy dla typu z oryginalnego zestawu do zestawu docelowego.  
  
2. W zestawie, w którym używany jest typ, Dodaj <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> dla typu, który został przeniesiony. Poniższy kod przedstawia atrybut dla typu o nazwie `Example` , który został przeniesiony.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3. Kompiluj zestaw, który zawiera teraz typ.  
  
4. Ponownie skompiluj zestaw, w którym znajduje się typ, z odwołaniem do zestawu, który zawiera teraz typ. Na przykład, Jeśli kompilujesz C# plik z wiersza polecenia, użyj opcji [/Reference (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) , aby określić zestaw, który zawiera typ. W C++programie użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Przekazywanie dalej typu (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using — dyrektywa](/cpp/preprocessor/hash-using-directive-cpp)
