---
title: Tagi zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: ef7ba44c0c3a8c660df9627361eb1cabdd9098a0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535960"
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
