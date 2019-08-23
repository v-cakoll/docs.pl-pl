---
title: -define (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: cb9de387b319ff4b81dcd1ccc37f04d8b6b3123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924797"
---
# <a name="-define-c-compiler-options"></a>-define (C# opcje kompilatora)
Opcja **-define** definiuje `name` jako symbol we wszystkich plikach kodu źródłowego tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `name`, `name2`  
 Nazwa co najmniej jednego symbolu, który ma zostać zdefiniowany.  
  
## <a name="remarks"></a>Uwagi  
 Opcja **-define** ma ten sam skutek jak użycie dyrektywy preprocesora [#define](../preprocessor-directives/preprocessor-define.md) , z wyjątkiem tego, że opcja kompilatora obowiązuje dla wszystkich plików w projekcie. Symbol pozostaje zdefiniowany w pliku źródłowym do momentu usunięcia definicji [#undef](../preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym. W przypadku użycia opcji `#undef` -define dyrektywa w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.  
  
 Możesz użyć symboli utworzonych przez tę opcję z [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)i [#endif](../preprocessor-directives/preprocessor-endif.md) , aby warunkowo kompilować pliki źródłowe.  
  
 **-d** jest krótką formą **-define**.  
  
 Można zdefiniować wiele symboli z **-Definiuj** przy użyciu średnika lub przecinka do oddzielenia nazw symboli. Przykład:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Sam C# kompilator definiuje nie symboli ani makr, których można użyć w kodzie źródłowym; wszystkie definicje symboli muszą być zdefiniowane przez użytkownika.  
  
> [!NOTE]
> Nie zezwala symbolowi na podaną wartość, jak w językach, takich jak C++ C# `#define` Na przykład `#define` nie można użyć do utworzenia makra lub zdefiniowania stałej. Jeśli musisz zdefiniować stałą, użyj `enum` zmiennej. Jeśli chcesz utworzyć makro C++ stylu, weź pod uwagę alternatywy, takie jak typy ogólne. Ponieważ makra są wielowątkowy bardzo podatne na błędy, C# nie zezwalają na ich użycie, ale zapewniają bezpieczniejsze alternatywy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Na karcie **kompilacja** wpisz symbol, który ma być zdefiniowany w polu **symbole kompilacji warunkowej** . Na przykład, jeśli używasz poniższego przykładu kodu, po prostu wpisz `xx` w polu tekstowym.  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
