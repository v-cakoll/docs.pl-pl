---
title: cref — C# Podręcznik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 2a9b9966a28b62c41ac6091268ae172bae3a40d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793442"
---
# <a name="cref-attribute-c-programming-guide"></a>cref — atrybutC# (Przewodnik programowania)

Atrybut `cref` w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość. Narzędzia do dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) , używają atrybutów `cref`, aby automatycznie generować hiperłącza do strony, na której jest udokumentowany typ lub element członkowski.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje `cref` atrybuty używane w [\<Zobacz tagi >](./see.md) .

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

Po skompilowaniu program tworzy następujący plik XML. Zwróć uwagę, że atrybut `cref` dla metody `GetZero`, na przykład, został przekształcony przez kompilator, aby `"M:TestNamespace.TestClass.GetZero"`. Prefiks "M:" oznacza "metodę" i jest konwencją, która jest rozpoznawana przez narzędzia dokumentacji, takie jak DocFX i Sandcastle. Aby uzyskać pełną listę prefiksów, zobacz [przetwarzanie pliku XML](./processing-the-xml-file.md).

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor">
            <summary>
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">
            <summary>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.GetZero">
            <summary>
            The GetZero method.
            </summary>
            <example> 
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.
            <code>
            class TestClass 
            {
                static int Main() 
                {
                    return GetZero();
                }
            }
            </code>
            </example>
        </member>
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">
            <summary>
            The GetGenericValue method.
            </summary>
            <remarks> 
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.
            </remarks>
        </member>
        <member name="T:TestNamespace.GenericClass`1">
            <summary>
            GenericClass.
            </summary>
            <remarks> 
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.
            </remarks>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>Zobacz także

- [Komentarze dokumentacji XML](./index.md)
- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
