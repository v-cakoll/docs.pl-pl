---
title: Przekazywanie typu w środowisku uruchomieniowym języka wspólnego
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f71b56daf5e8a012a66f60805246b4164d1b0a07
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973020"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Przekazywanie typu w środowisku uruchomieniowym języka wspólnego
Przekazywanie typu pozwala przenieść typ do innego zestawu bez konieczności ponownego kompilowania aplikacji, które używają oryginalnego zestawu.  
  
 Załóżmy na przykład, że aplikacja używa `Example` klasy w zestawie o nazwie *Utility. dll*. Deweloperzy *Narzędzia Utility. dll* mogą zdecydować się na refaktoryzację zestawu, a w procesie może przenieść `Example` klasę do innego zestawu. Jeśli stara wersja *Narzędzia Utility. dll* jest zastępowana przez nową wersję *pliku Utility. dll* i jego zestawu towarzyszącego, aplikacja `Example` , która używa klasy, `Example` kończy się niepowodzeniem, ponieważ nie może zlokalizować klasy w nowej wersji programu.  *Narzędzie. dll*.  
  
 Deweloperzy *Narzędzia Utility. dll* mogą uniknąć tego przez przekazywanie żądań dla `Example` <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> klasy przy użyciu atrybutu. Jeśli atrybut został zastosowany do nowej wersji *pliku Utility. dll*, żądania dla `Example` klasy są przekazywane do zestawu, który zawiera teraz klasę. Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 nie można przesłać dalej typów z zestawów utworzonych w Visual Basic. Jednak aplikacja zapisywana w Visual Basic może korzystać z przekazanych typów. Oznacza to, że jeśli aplikacja używa zestawu zakodowanego w C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może użyć przekazanego typu.  
  
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
   
4. Ponownie skompiluj zestaw, w którym znajduje się typ, z odwołaniem do zestawu, który zawiera teraz typ. Na przykład, Jeśli kompilujesz C# plik z wiersza polecenia, użyj opcji [/Reference (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) , aby określić zestaw, który zawiera typ. W C++programie użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Przekazywanie typu (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [#using — dyrektywa](/cpp/preprocessor/hash-using-directive-cpp)
