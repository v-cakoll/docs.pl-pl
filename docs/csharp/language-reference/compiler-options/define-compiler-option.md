---
title: -Definiowanie (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d4c7e4e646e6796cff6bbfbe05038ff361fa80c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-compiler-options"></a>/define (opcje kompilatora C#)
**/ Define** opcja definiuje `name` jako symbol w kodzie źródłowym wszystkie pliki programu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/define:name[;name2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `name`, `name2`  
 Nazwa jednego lub wielu symboli, które chcesz zdefiniować.  
  
## <a name="remarks"></a>Uwagi  
 **/ Define** opcja działa tak samo jak przy użyciu [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy preprocesora z tą różnicą, że opcja kompilatora jest włączona dla wszystkich plików w projekcie. Symbol pozostaje zdefiniowane w pliku źródłowym do [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) dyrektywy w pliku źródłowym usuwa definicję. Jeśli używasz / define — opcja, `#undef` dyrektywy w jednym pliku nie ma wpływu na inne pliki kodu źródłowego w projekcie.  
  
 Można użyć symboli utworzone przez tę opcję z [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), i [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) warunkowo skompilować plików źródłowych.  
  
 **/d** jest krótka forma **/ define**.  
  
 Można zdefiniować wiele symboli z **/ define** przy użyciu symbolu nazwy średnikami lub przecinkami. Na przykład:  
  
```console  
/define:DEBUG;TUESDAY  
```  
  
 Kompilator języka C#, sam definiuje nie symboli lub makra używane w kodzie źródłowym; wszystkie definicje symbolu muszą być zdefiniowane przez użytkownika.  
  
> [!NOTE]
>  C# `#define` nie zezwala na symbolu, należy podać wartość, jak języków, takich jak C++. Na przykład `#define` nie może służyć do tworzenia makr lub zdefiniuj stałą. Jeśli musisz zdefiniować stałą, użyj `enum` zmiennej. Jeśli chcesz utworzyć makro styl C++, należy wziąć pod uwagę rozwiązań alternatywnych, takich jak ogólne. Ponieważ makra są bardzo podatne na błędy, C# nie zezwala na ich użycia, ale zapewnia bezpieczniejszych alternatyw.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Na **kompilacji** , wpisz symbol, który ma być zdefiniowana w **symbole kompilacji warunkowej** pole. Na przykład, jeśli używasz przykładowy kod, który następuje po prostu wpisz `xx` w polu tekstowym.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a>Przykład  
  
```csharp  
// preprocessor_define.cs  
// compile with: /define:xx  
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
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
