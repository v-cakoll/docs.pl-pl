---
title: -Definiowanie (opcje kompilatora C#)
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
ms.openlocfilehash: 56028bcf3b843a4f6884e2d7cc7d409621adba34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558822"
---
# <a name="-define-c-compiler-options"></a>-Definiowanie (opcje kompilatora C#)
**— Zdefiniuj** opcja definiuje `name` jako symbol w kodzie źródłowym wszystkie pliki programu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `name`, `name2`  
 Nazwa co najmniej jeden symboli, które chcesz zdefiniować.  
  
## <a name="remarks"></a>Uwagi  
 **— Zdefiniuj** opcja ma taki sam skutek jak przy użyciu [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora z tą różnicą, że opcja kompilatora jest aktywna dla wszystkich plików w projekcie. Symbol pozostaje zdefiniowany w pliku źródłowym, dopóki [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym usuwa definicję. Jeśli używasz define — opcja, `#undef` dyrektywy w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.  
  
 Można użyć symboli utworzone przez tę opcję z [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), i [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) Aby warunkowo skompilować pliki źródłowe.  
  
 **-d** jest krótka forma **— Zdefiniuj**.  
  
 Można zdefiniować wiele symboli z **— Zdefiniuj** przy użyciu nazwy symbolu średnikami lub przecinkami. Na przykład:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 Kompilator języka C#, sama definiuje nie symboli lub makra używane w kodzie źródłowym; wszystkie definicje symboli muszą być zdefiniowane przez użytkownika.  
  
> [!NOTE]
>  C# `#define` nie zezwala na symbol należy podać wartości, tak jak w językach takich jak C++. Na przykład `#define` nie można użyć, aby utworzyć makro lub aby zdefiniować stałą. Jeśli potrzebujesz zdefiniować stałą, użyj `enum` zmiennej. Jeśli chcesz utworzyć makro styl C++, należy wziąć pod uwagę rozwiązań alternatywnych, takich jak typy ogólne. Ponieważ makra są bardzo podatne na błędy, C# nie zezwalają na ich użycia, ale zapewnia bezpieczniejszych alternatyw.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Na **kompilacji** karty, wpisz symbol, który ma zostać określona w **symbole kompilacji warunkowej** pole. Na przykład, jeśli używasz przykładu kodu, który następuje po prostu wpisz `xx` w polu tekstowym.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
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

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
