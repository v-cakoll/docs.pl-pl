---
title: -define (Opcje kompilatora C#)
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
ms.openlocfilehash: 4a3622b6acc8ebe9c590b01b67074ae59396fc34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173747"
---
# <a name="-define-c-compiler-options"></a>-define (Opcje kompilatora C#)
Opcja **-define** definiuje `name` jako symbol we wszystkich plikach kodu źródłowego programu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `name`, `name2`  
 Nazwa jednego lub więcej symboli, które chcesz zdefiniować.  
  
## <a name="remarks"></a>Uwagi  
 **Opcja -define** ma taki sam efekt jak przy użyciu #define dyrektywy preprocesora, z tą różnicą, że opcja kompilatora obowiązuje dla wszystkich plików w projekcie. [#define](../preprocessor-directives/preprocessor-define.md) Symbol pozostaje zdefiniowany w pliku źródłowym, dopóki [#undef](../preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym nie usunie definicji. Korzystając z opcji -define, `#undef` dyrektywa w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.  
  
 Symboli utworzonych przez tę opcję można używać za pomocą [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md)i [#endif](../preprocessor-directives/preprocessor-endif.md) do warunkowego kompilowania plików źródłowych.  
  
 **-d** jest krótką formą **-define**.  
  
 Można zdefiniować wiele symboli za pomocą **-define** za pomocą średnika lub przecinka do oddzielania nazw symboli. Przykład:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Kompilator Języka C# sam definiuje żadnych symboli lub makr, których można użyć w kodzie źródłowym; wszystkie definicje symboli muszą być zdefiniowane przez użytkownika.  
  
> [!NOTE]
> C# `#define` nie zezwala na symbol, aby otrzymać wartość, jak w językach, takich jak C++. Na przykład `#define` nie można użyć do utworzenia makra lub do zdefiniowania stałej. Jeśli trzeba zdefiniować stałą, `enum` należy użyć zmiennej. Jeśli chcesz utworzyć makro stylu C++, rozważ alternatywy, takie jak generycznych. Ponieważ makra są notorycznie podatne na błędy, C# nie zezwala na ich użycie, ale zapewnia bezpieczniejsze alternatywy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Na **karcie Kompilacja** wpisz symbol, który ma być zdefiniowany w polu **Symbole kompilacji warunkowej.** Na przykład jeśli używasz przykładu kodu, który `xx` następuje, wystarczy wpisać w polu tekstowym.  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>kompilatora, zobacz .  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
