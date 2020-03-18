---
title: <summary> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789674"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="408c0-102">\<podsumowanie> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="408c0-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="408c0-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="408c0-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="408c0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="408c0-104">Parameters</span></span>

- `description`

  <span data-ttu-id="408c0-105">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="408c0-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="408c0-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="408c0-106">Remarks</span></span>

<span data-ttu-id="408c0-107">Tag \<> podsumowania powinien być używany do opisywania typu lub elementu członkowskiego typu.</span><span class="sxs-lookup"><span data-stu-id="408c0-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="408c0-108">Użyj [ \<uwag>,](./remarks.md) aby dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="408c0-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="408c0-109">Użyj [atrybutu cref,](./cref-attribute.md) aby włączyć narzędzia dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle,](https://github.com/EWSoftware/SHFB) aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.</span><span class="sxs-lookup"><span data-stu-id="408c0-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="408c0-110">Tekst \<podsumowania> tagu jest jedynym źródłem informacji o typie w intelliSense i jest również wyświetlany w oknie przeglądarki obiektów.</span><span class="sxs-lookup"><span data-stu-id="408c0-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="408c0-111">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="408c0-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="408c0-112">Aby utworzyć ostateczną dokumentację na podstawie pliku wygenerowanego przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="408c0-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="408c0-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="408c0-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="408c0-114">Poprzedni przykład tworzy następujący plik XML.</span><span class="sxs-lookup"><span data-stu-id="408c0-114">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="408c0-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="408c0-115">Example</span></span>

<span data-ttu-id="408c0-116">W poniższym przykładzie pokazano, jak odwołać się `cref` do typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="408c0-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="408c0-117">Poprzedni przykład tworzy następujący plik XML.</span><span class="sxs-lookup"><span data-stu-id="408c0-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="408c0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="408c0-118">See also</span></span>

- [<span data-ttu-id="408c0-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="408c0-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="408c0-120">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="408c0-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
