---
title: Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160368"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Przekazywanie dalej typu w środowisku uruchomieniowym języka wspólnego
Przekazywanie tekstu umożliwia przeniesienie typu do innego zestawu bez konieczności ponownej kompilacji aplikacji korzystających z oryginalnego zestawu.  
  
 Załóżmy na przykład, `Example` że aplikacja używa klasy w zestawie o nazwie *Utility.dll*. Deweloperzy *Utility.dll* może zdecydować się na refaktoryzacji zestawu, `Example` a w procesie mogą przenieść klasy do innego zestawu. Jeśli stara wersja *pliku Utility.dll* zostanie zastąpiona nową wersją *pliku Utility.dll* i jej zestawu towarzyszącego, aplikacja korzystająca z `Example` tej klasy nie powiedzie się, ponieważ nie może zlokalizować `Example` klasy w nowej wersji pliku *Utility.dll*.  
  
 Deweloperzy *Utility.dll* można tego uniknąć, przesyłając dalej żądania dla `Example` klasy, przy użyciu atrybutu. <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> Jeśli atrybut został zastosowany do nowej wersji *Utility.dll,* żądania dla `Example` klasy są przekazywane do zestawu, który teraz zawiera klasę. Istniejąca aplikacja nadal działa normalnie, bez ponownej kompilacji.  
  
> [!NOTE]
> W wersji .NET Framework w wersji 2.0 nie można przesyłać dalej typów z zestawów napisanych w języku Visual Basic. Jednak aplikacja napisana w języku Visual Basic może korzystać z typów przesyłanych dalej. Oznacza to, że jeśli aplikacja używa zestawu zakodowanego w języku C# lub C++, a typ z tego zestawu jest przekazywany do innego zestawu, aplikacja Visual Basic może używać typu przekazywanego dalej.  
  
## <a name="forward-types"></a>Typy do przodu  
 Istnieją cztery kroki przekazywania typu:  
  
1. Przenieś kod źródłowy typu z oryginalnego złożenia do zestawu docelowego.  

2. W zestawie, w którym typ był <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> używany, dodaj a dla typu, który został przeniesiony. Poniższy kod przedstawia atrybut dla `Example` typu o nazwie, który został przeniesiony.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Skompiluj zestaw, który teraz zawiera typ.  

4. Ponownie skompilować zestaw, w którym typ był używany, z odwołaniem do zestawu, który teraz zawiera typ. Na przykład jeśli kompilowanie pliku C# z wiersza polecenia, użyj [-reference (Opcje kompilatora C#),](../../csharp/language-reference/compiler-options/reference-compiler-option.md) aby określić zestaw, który zawiera typ. W języku C++ użyj dyrektywy [#using](/cpp/preprocessor/hash-using-directive-cpp) w pliku źródłowym, aby określić zestaw, który zawiera typ.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Przekazywanie tekstu (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [dyrektywa #using](/cpp/preprocessor/hash-using-directive-cpp)
