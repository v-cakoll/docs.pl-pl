---
title: <include> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 125ab9476507babae9a707a6c42d24adda632267
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696561"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="81c83-102">\<Uwzględnij >C# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="81c83-102">\<include> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="81c83-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="81c83-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a><span data-ttu-id="81c83-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="81c83-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="81c83-105">Nazwa pliku XML zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="81c83-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="81c83-106">Nazwa pliku może być kwalifikowana ze ścieżką względną do pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="81c83-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="81c83-107">Ujmij `filename` w znaki pojedynczego cudzysłowu (' ').</span><span class="sxs-lookup"><span data-stu-id="81c83-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="81c83-108">Ścieżka tagów w `filename`, które prowadzą do `name`znacznika.</span><span class="sxs-lookup"><span data-stu-id="81c83-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="81c83-109">Ujmij ścieżkę w znaki pojedynczego cudzysłowu (' ').</span><span class="sxs-lookup"><span data-stu-id="81c83-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="81c83-110">Specyfikator nazwy w tagu, który poprzedza Komentarze; `name` będzie `id`.</span><span class="sxs-lookup"><span data-stu-id="81c83-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="81c83-111">Identyfikator tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="81c83-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="81c83-112">Ujmij identyfikator w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="81c83-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81c83-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81c83-113">Remarks</span></span>  
 <span data-ttu-id="81c83-114">\<include tag > umożliwia odwoływanie się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="81c83-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="81c83-115">Jest to alternatywa dla umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="81c83-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="81c83-116">Umieszczając dokumentację w osobnym pliku, można zastosować kontrolę źródła do dokumentacji niezależnie od kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="81c83-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="81c83-117">Jedna osoba może mieć wyewidencjonowany plik kodu źródłowego, a ktoś inny może mieć wyewidencjonowany plik dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="81c83-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="81c83-118">\<include tag > używa składni XML XPath.</span><span class="sxs-lookup"><span data-stu-id="81c83-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="81c83-119">Zapoznaj się z dokumentacją XPath, aby dostosowywać \<obejmują > Użycie.</span><span class="sxs-lookup"><span data-stu-id="81c83-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81c83-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="81c83-120">Example</span></span>  
 <span data-ttu-id="81c83-121">Jest to przykład wieloplikowy.</span><span class="sxs-lookup"><span data-stu-id="81c83-121">This is a multifile example.</span></span> <span data-ttu-id="81c83-122">Pierwszy plik, który używa \<zawiera >, jest wymieniony poniżej:</span><span class="sxs-lookup"><span data-stu-id="81c83-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 <span data-ttu-id="81c83-123">Drugi plik, xml_include_tag. doc, zawiera następujące komentarze dokumentacji:</span><span class="sxs-lookup"><span data-stu-id="81c83-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
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
  
## <a name="program-output"></a><span data-ttu-id="81c83-124">Dane wyjściowe programu</span><span class="sxs-lookup"><span data-stu-id="81c83-124">Program Output</span></span>  
 <span data-ttu-id="81c83-125">Następujące dane wyjściowe są generowane podczas kompilowania klas test i TEST2 z następującym wierszem polecenia: `/doc:DocFileName.xml.` w programie Visual Studio, należy określić opcję komentarzy w dokumencie XML w okienku kompilacja projektanta projektu.</span><span class="sxs-lookup"><span data-stu-id="81c83-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="81c83-126">Gdy C# kompilator widzi tag \<include >, będzie wyszukiwał komentarze dokumentacji w xml_include_tag. doc zamiast bieżącego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="81c83-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="81c83-127">Następnie kompilator generuje DocFileName. XML i jest to plik, który jest używany przez narzędzia dokumentacji, takie jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) , aby utworzyć ostateczną dokumentację.</span><span class="sxs-lookup"><span data-stu-id="81c83-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81c83-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81c83-128">See also</span></span>

- [<span data-ttu-id="81c83-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="81c83-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="81c83-130">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="81c83-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
