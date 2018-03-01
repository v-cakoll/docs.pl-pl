---
title: "cref — Atrybut (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cffba9083b22813be3dd0379b244f4d078f8549
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="e1684-102">cref — Atrybut (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e1684-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="e1684-103">`cref` Atrybut w tagu XML dokumentacji oznacza "kodu odwołania."</span><span class="sxs-lookup"><span data-stu-id="e1684-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="e1684-104">Określa on, że tekst wewnętrzny tagu jest element kodu, takie jak typ, metoda lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="e1684-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="e1684-105">Dokumentacja narzędzi, takich jak [Sandcastle](https://github.com/EWSoftware/SHFB) użyj `cref` atrybutów w celu automatycznego generowania hiperłącza do strony, której typ lub element członkowski jest udokumentowany.</span><span class="sxs-lookup"><span data-stu-id="e1684-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1684-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1684-106">Example</span></span>  
 <span data-ttu-id="e1684-107">W poniższym przykładzie przedstawiono `cref` atrybuty używane w [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md) tagów.</span><span class="sxs-lookup"><span data-stu-id="e1684-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]  
  
 <span data-ttu-id="e1684-108">Podczas kompilacji, program tworzy następującego pliku XML.</span><span class="sxs-lookup"><span data-stu-id="e1684-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="e1684-109">Zwróć uwagę, że `cref` atrybutu dla `GetZero` metody została przekształcona na przykład przez kompilator, aby `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="e1684-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="e1684-110">Prefiks "M" oznacza "method" i Konwencji, który jest rozpoznawany przez dokumentacji narzędzi, takich jak Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="e1684-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="e1684-111">Aby uzyskać pełną listę prefiksów, zobacz [przetwarzanie pliku XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="e1684-111">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1684-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1684-112">See Also</span></span>  
 [<span data-ttu-id="e1684-113">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="e1684-113">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="e1684-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e1684-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
