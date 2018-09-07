---
title: '&lt;Podsumowanie&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: cd52d68a5b59648aa2253c515dabd334c22dad5d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061562"
---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="f1781-102">&lt;Podsumowanie&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f1781-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f1781-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1781-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1781-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1781-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="f1781-105">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f1781-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1781-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1781-106">Remarks</span></span>  
 <span data-ttu-id="f1781-107">\<Podsumowania > tag powinien być używany do opisu typu lub składowej typu.</span><span class="sxs-lookup"><span data-stu-id="f1781-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="f1781-108">Użyj [ \<Uwagi >](../../../csharp/programming-guide/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="f1781-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="f1781-109">Użyj [cref — atrybut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) umożliwiające dokumentacji narzędzia, takie jak [Sandcastle](https://github.com/EWSoftware/SHFB) do utworzenia wewnętrznego hiperlinki do stron dokumentacji dla elementów kodu.</span><span class="sxs-lookup"><span data-stu-id="f1781-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="f1781-110">Tekst dla \<podsumowania > tag to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany w oknie przeglądarki obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1781-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="f1781-111">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="f1781-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="f1781-112">Aby utworzyć dokumentację na podstawie pliku generowanych przez kompilator, można utworzyć narzędzie niestandardowe, lub użyj narzędzia takiego jak [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="f1781-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1781-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1781-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 <span data-ttu-id="f1781-114">Poprzedni przykład tworzy następującego pliku XML.</span><span class="sxs-lookup"><span data-stu-id="f1781-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="f1781-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1781-115">Example</span></span>  
 <span data-ttu-id="f1781-116">Poniższy przykład pokazuje, jak wprowadzić `cref` odwołanie do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f1781-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 <span data-ttu-id="f1781-117">Poprzedni przykład tworzy następującego pliku XML.</span><span class="sxs-lookup"><span data-stu-id="f1781-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1781-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1781-118">See Also</span></span>

- [<span data-ttu-id="f1781-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f1781-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f1781-120">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="f1781-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
