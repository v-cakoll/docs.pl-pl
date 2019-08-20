---
title: cref — C# Podręcznik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: d088e1fcd0a1d1910b1284909dccf7b7d7b1d479
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588168"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="f865d-102">cref — Atrybut (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f865d-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="f865d-103">`cref` Atrybut w tagu dokumentacji XML oznacza "odwołanie do kodu".</span><span class="sxs-lookup"><span data-stu-id="f865d-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="f865d-104">Określa, że wewnętrznym tekstem znacznika jest element kodu, taki jak typ, metoda lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="f865d-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="f865d-105">Narzędzia do dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i `cref` [Sandcastle](https://github.com/EWSoftware/SHFB) , używają atrybutów do automatycznego generowania hiperłączy do strony, na której jest udokumentowany typ lub element członkowski.</span><span class="sxs-lookup"><span data-stu-id="f865d-105">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f865d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f865d-106">Example</span></span>  
 <span data-ttu-id="f865d-107">Poniższy przykład pokazuje `cref` atrybuty używane w [ \<Zobacz >](./see.md) Tagi.</span><span class="sxs-lookup"><span data-stu-id="f865d-107">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]  
  
 <span data-ttu-id="f865d-108">Po skompilowaniu program tworzy następujący plik XML.</span><span class="sxs-lookup"><span data-stu-id="f865d-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="f865d-109">Zwróć uwagę, `cref` że atrybut `GetZero` metody, na przykład, został przekształcony przez kompilator na `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="f865d-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="f865d-110">Prefiks "M:" oznacza "metodę" i jest konwencją, która jest rozpoznawana przez narzędzia dokumentacji, takie jak DocFX i Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="f865d-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="f865d-111">Aby uzyskać pełną listę prefiksów, zobacz [przetwarzanie pliku XML](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f865d-111">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
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
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
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
  
## <a name="see-also"></a><span data-ttu-id="f865d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f865d-112">See also</span></span>

- [<span data-ttu-id="f865d-113">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="f865d-113">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="f865d-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="f865d-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
