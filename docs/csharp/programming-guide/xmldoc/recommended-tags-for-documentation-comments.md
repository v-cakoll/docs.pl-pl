---
title: Tagi zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 54047746db672efbf626eb2d3fc301b341cc49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Tagi zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)
Kompilator języka C# przetwarza komentarze do dokumentacji w kodzie i formatuje je jako kod XML w pliku o nazwie określonej w **/doc** opcji wiersza polecenia. Aby utworzyć końcowego dokumentację na podstawie pliku generowane przez kompilator, można utworzyć niestandardowego narzędzia, lub za pomocą narzędzia, takie jak [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Tagi są przetwarzane w konstrukcji kodu, takie jak typy i elementy członkowskie typu.  
  
> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw.  
  
 Kompilator będzie przetwarzać wszystkie tag, który jest prawidłowym kodem XML. Następujące znaczniki udostępniają funkcje zwykle używanych w dokumentacji użytkownika.  
  
## <a name="tags"></a>Znaczniki  
  
||||  
|---|---|---|  
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<zobacz >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<Kod >](../../../csharp/programming-guide/xmldoc/code.md)|[\<param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<SeeAlso >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<przykład >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<wyjątku >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<uprawnienie >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<obejmują >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<Remarks >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list>](../../../csharp/programming-guide/xmldoc/list.md)|[\<Zwraca >](../../../csharp/programming-guide/xmldoc/returns.md)|[\<wartość >](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* oznacza, że kompilator sprawdza składnię.)  
  
 Nawiasy się pojawić w tekście komentarza do dokumentacji, należy użyć `<` i `>`, jak pokazano w poniższym przykładzie.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
