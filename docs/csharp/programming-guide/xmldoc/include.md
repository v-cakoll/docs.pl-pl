---
title: <include> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 22d87559766c04e53141e843ee8768c8aab89a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156977"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="0bd2b-102">\<obejmują> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="0bd2b-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bd2b-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bd2b-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="0bd2b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bd2b-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="0bd2b-105">Nazwa pliku XML zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="0bd2b-106">Nazwę pliku można zakwalifikować ścieżką względem pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="0bd2b-107">Zacofij `filename` w pojedynczych cudzysłowu ('').</span><span class="sxs-lookup"><span data-stu-id="0bd2b-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="0bd2b-108">Ścieżka znaczników `filename` w tym prowadzi `name`do tagu .</span><span class="sxs-lookup"><span data-stu-id="0bd2b-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="0bd2b-109">Ścieżkę ująć w pojedyncze cudzysłowy (' ').</span><span class="sxs-lookup"><span data-stu-id="0bd2b-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="0bd2b-110">Specyfikator nazw w tagu, który poprzedza komentarze; `name` będzie miał `id`.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="0bd2b-111">Identyfikator tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="0bd2b-112">Identyfikator ujmij w cudzysłów podwójny (" ").</span><span class="sxs-lookup"><span data-stu-id="0bd2b-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="0bd2b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bd2b-113">Remarks</span></span>

<span data-ttu-id="0bd2b-114">Tag \<> include umożliwia odwoływanie się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="0bd2b-115">Jest to alternatywa dla umieszczania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="0bd2b-116">Umieszczając dokumentację w oddzielnym pliku, można zastosować kontrolę źródła do dokumentacji oddzielnie od kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="0bd2b-117">Jedna osoba może wyewidencjonować plik kodu źródłowego, a ktoś inny może wyewidencjonować plik dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="0bd2b-118">Tag \<> dołączania używa składni XML XPath.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="0bd2b-119">W dokumentacji XPath można \<znaleźć sposoby dostosowywania> użycia.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>

## <a name="example"></a><span data-ttu-id="0bd2b-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bd2b-120">Example</span></span>

<span data-ttu-id="0bd2b-121">Jest to przykład wieloplikowy.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-121">This is a multifile example.</span></span> <span data-ttu-id="0bd2b-122">Poniżej przedstawiono pierwszy plik, \<który używa obejmują>.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-122">The following is the first file, which uses \<include>.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="0bd2b-123">Drugi plik, *xml_include_tag.doc,* zawiera następujące komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a><span data-ttu-id="0bd2b-124">Dane wyjściowe programu</span><span class="sxs-lookup"><span data-stu-id="0bd2b-124">Program output</span></span>

<span data-ttu-id="0bd2b-125">Następujące dane wyjściowe są generowane podczas kompilowania testów i testów2 klas z następującym wierszem polecenia: `-doc:DocFileName.xml.` W programie Visual Studio można określić opcję komentarze doc XML w okienku kompilacji projektanta projektu.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="0bd2b-126">Gdy kompilator Języka \<C# widzi include> tag, będzie wyszukiwać komentarze dokumentacji w xml_include_tag.doc zamiast bieżącego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="0bd2b-127">Kompilator następnie generuje DocFileName.xml, a jest to plik, który jest używany przez narzędzia dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do produkcji ostatecznej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="0bd2b-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.
</summary>
        </member>
        <member name="T:Test2">
            <summary>
The summary for this other type.
</summary>
        </member>
    </members>
</doc>
```  
  
## <a name="see-also"></a><span data-ttu-id="0bd2b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bd2b-128">See also</span></span>

- [<span data-ttu-id="0bd2b-129">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0bd2b-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0bd2b-130">Zalecane tagi do komentarzy do dokumentacji</span><span class="sxs-lookup"><span data-stu-id="0bd2b-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
