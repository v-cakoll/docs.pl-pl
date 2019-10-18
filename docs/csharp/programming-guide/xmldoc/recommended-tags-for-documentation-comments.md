---
title: Zalecane Tagi dla komentarzy do dokumentacji C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: d17ff0b78d8ae40916447e8e12da7948a21e5717
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523371"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Znaczniki zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)
Kompilator przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwa została określona w opcji wiersza polecenia **/doc.** C# Aby utworzyć ostateczną dokumentację opartą na pliku generowanym przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.  
  
> [!NOTE]
> Komentarzy do dokumentacji nie można zastosować do przestrzeni nazw.  
  
 Kompilator będzie przetwarzać dowolny tag, który jest prawidłowym kodem XML. Poniższe Tagi zapewniają ogólnie używane funkcje w dokumentacji użytkownika.  
  
## <a name="tags"></a>Znaczniki  
  
||||  
|---|---|---|  
|[\<c >](./code-inline.md)|[\<para >](./para.md)|[\<see >](./see.md) *|  
|[\<code >](./code.md)|[\<param >](./param.md) *|[\<seealso >](./seealso.md) *|  
|[\<example >](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception >](./exception.md) *|[\<permission >](./permission.md) *|[\<typeparam >](./typeparam.md) *|  
|[\<include >](./include.md) *|[\<remarks >](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<list >](./list.md)|[\<returns>](./returns.md)|[\<value>](./value.md)|  
  
 (* wskazuje, że kompilator weryfikuje składnię).  
  
 Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj kodowania HTML `<` i `>` `&lt;` i `&gt;` odpowiednio. To kodowanie pokazano w następującym przykładzie:
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [-doc (C# opcje kompilatora)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Komentarze dokumentacji XML](./index.md)
