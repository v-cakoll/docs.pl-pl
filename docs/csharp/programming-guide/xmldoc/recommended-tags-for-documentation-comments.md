---
title: Zalecane Tagi dla komentarzy do dokumentacji C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 15a183d72a7d3e47f99227cea2cf870ad2f98d18
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696535"
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
|[\<c>](./code-inline.md)|[\<para >](./para.md)|[\<see>](./see.md)*|  
|[> kodu \<](./code.md)|[\<param >](./param.md)*|[\<seealso>](./seealso.md)*|  
|[przykład \<](./example.md)|[\<paramref >](./paramref.md)|[\<summary>](./summary.md)|  
|[\<> wyjątków](./exception.md)*|[> uprawnień\<](./permission.md)*|[\<typeparam >](./typeparam.md)*|  
|[\<uwzględnić >](./include.md)*|[\<uwagi >](./remarks.md)|[\<typeparamref >](./typeparamref.md)|  
|[\<list>](./list.md)|[\<returns>](./returns.md)|[\<value>](./value.md)|  
  
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
