---
title: atrybut cref - przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: b06d0c9d447124dec7d8cf3c0cbbfd0daca78fe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157016"
---
# <a name="cref-attribute-c-programming-guide"></a>atrybut cref (przewodnik programowania C#)

Atrybut `cref` w tagu dokumentacji XML oznacza "odwołanie do kodu". Określa, że wewnętrzny tekst znacznika jest elementem kodu, takim jak typ, metoda lub właściwość. Narzędzia dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle,](https://github.com/EWSoftware/SHFB) używają atrybutów do automatycznego `cref` generowania hiperłączy do strony, na której typ lub element członkowski jest udokumentowany.

## <a name="example"></a>Przykład

W poniższym `cref` przykładzie przedstawiono atrybuty używane w [ \<znacznikach>.](./see.md)

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

Po skompilowaniu program tworzy następujący plik XML. Należy zauważyć, `cref` że `GetZero` atrybut dla metody, na przykład, został `"M:TestNamespace.TestClass.GetZero"`przekształcony przez kompilator do . Przedrostek "M:" oznacza "metoda" i jest konwencją rozpoznawaną przez narzędzia dokumentacji, takie jak DocFX i Sandcastle. Aby uzyskać pełną listę prefiksów, zobacz [Przetwarzanie pliku XML](./processing-the-xml-file.md).

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

## <a name="see-also"></a>Zobacz też

- [Komentarze dokumentacji XML](./index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)
