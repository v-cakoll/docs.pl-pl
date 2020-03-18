---
title: Zalecane tagi do komentarzy dokumentacji - Przewodnik programowania C#
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789727"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Zalecane tagi komentarzy do dokumentacji (przewodnik programowania Języka C#)

Kompilator Języka C# przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwę określisz w opcji wiersza polecenia **/doc.** Aby utworzyć ostateczną dokumentację na podstawie pliku wygenerowanego przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).

Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.

> [!NOTE]
> Nie można zastosować komentarzy dokumentacji do obszaru nazw.  
  
 Kompilator przetworzy dowolny tag, który jest prawidłowy mś. Następujące tagi zawierają ogólnie używane funkcje w dokumentacji użytkownika.  
  
## <a name="tags"></a>Tagi  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<zobacz>](./see.md)*|[\<wartość>](./value.md)  
|[\<>kodu](./code.md)|[\<param>](./param.md)*|[\<>](./seealso.md)*|  
|[\<przykład>](./example.md)|[\<paramref>](./paramref.md)|[\<>podsumowującym](./summary.md)|  
|[\<>wyjątek](./exception.md)*|[\<>uprawnień](./permission.md)*|[\<>typuparam](./typeparam.md)*|  
|[\<obejmują>](./include.md)*|[\<uwagi>](./remarks.md)|[\<typparamref>](./typeparamref.md)|  
|[\<>listy](./list.md)|[\<dziedzic>zenia](./inheritdoc.md)|[\<zwraca>](./returns.md)|
  
(\* oznacza, że kompilator weryfikuje składnię.)

Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście `<` `>` komentarza `&lt;` do `&gt;` dokumentacji, użyj kodowania HTML, a który jest i jest odpowiednio. To kodowanie jest pokazane w poniższym przykładzie.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (opcje kompilatora C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
