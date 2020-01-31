---
title: Zalecane Tagi dla komentarzy do dokumentacji C# — Przewodnik programowania
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789727"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Zalecane Tagi dla komentarzy do dokumentacjiC# (Przewodnik programowania)

Kompilator przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwa została określona w opcji wiersza polecenia **/doc.** C# Aby utworzyć ostateczną dokumentację opartą na pliku generowanym przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).

Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.

> [!NOTE]
> Komentarzy do dokumentacji nie można zastosować do przestrzeni nazw.  
  
 Kompilator będzie przetwarzać dowolny tag, który jest prawidłowym kodem XML. Poniższe Tagi zapewniają ogólnie używane funkcje w dokumentacji użytkownika.  
  
## <a name="tags"></a>Znaczniki  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para >](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[> kodu \<](./code.md)|[\<param >](./param.md)*|[\<seealso>](./seealso.md)*|  
|[przykład \<](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<> wyjątków](./exception.md)*|[> uprawnień\<](./permission.md)*|[\<typeparam >](./typeparam.md)*|  
|[\<uwzględnić >](./include.md)*|[\<uwagi >](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc >](./inheritdoc.md)|[\<returns>](./returns.md)|
  
(\* oznacza, że kompilator weryfikuje składnię).

Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj kodowania HTML `<` i `>` `&lt;` i `&gt;` odpowiednio. To kodowanie jest pokazane w poniższym przykładzie.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Zobacz także

- [C#Przewodnik programowania](../index.md)
- [-doc (C# opcje kompilatora)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
