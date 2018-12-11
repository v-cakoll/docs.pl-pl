---
title: Zalecane tagi przeznaczone do komentarzy dokumentacji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: fb4d8d4dde38d7cbe1b0434c290dd922b2e328a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245590"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Tagi zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)
Kompilator języka C# przetwarza komentarze dokumentacji w kodzie i sformatuje je jako kod XML w pliku o nazwie określonej w **/doc** opcji wiersza polecenia. Aby utworzyć dokumentację na podstawie pliku generowanych przez kompilator, można utworzyć narzędzie niestandardowe, lub użyj narzędzia takiego jak [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Tagi są przetwarzane na kodzie konstrukcji, takich jak typy i elementy członkowskie typu.  
  
> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw.  
  
 Kompilator przetworzy dowolnymi tagami, które jest prawidłowym kodem XML. Następujące znaczniki oferuje powszechnie używanych w dokumentacji użytkownika.  
  
## <a name="tags"></a>Znaczniki  
  
||||  
|---|---|---|  
|[\<c >](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para >](../../../csharp/programming-guide/xmldoc/para.md)|[\<zobacz >](../../../csharp/programming-guide/xmldoc/see.md)*|  
|[\<Kod >](../../../csharp/programming-guide/xmldoc/code.md)|[\<param >](../../../csharp/programming-guide/xmldoc/param.md)*|[\<SeeAlso — >](../../../csharp/programming-guide/xmldoc/seealso.md)*|  
|[\<przykład >](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref >](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<Summary >](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<wyjątku >](../../../csharp/programming-guide/xmldoc/exception.md)*|[\<uprawnienie >](../../../csharp/programming-guide/xmldoc/permission.md)*|[\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)*|  
|[\<obejmują >](../../../csharp/programming-guide/xmldoc/include.md)*|[\<Remarks >](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list>](../../../csharp/programming-guide/xmldoc/list.md)|[\<Zwraca wartość >](../../../csharp/programming-guide/xmldoc/returns.md)|[\<wartość >](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 (* oznacza, że kompilator sprawdza składnię.)  
  
 Nawiasy są wyświetlane w tekście komentarza do dokumentacji, użyć `<` i `>`, jak pokazano w poniższym przykładzie.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [/ doc (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [Komentarze dokumentacji XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
