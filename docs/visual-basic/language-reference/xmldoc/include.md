---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400114"
---
# <a name="include-visual-basic"></a><span data-ttu-id="a4c43-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4c43-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="a4c43-102">Odwołuje się do innego pliku opisującego typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="a4c43-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c43-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4c43-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4c43-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4c43-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="a4c43-105">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a4c43-105">Required.</span></span> <span data-ttu-id="a4c43-106">Nazwa pliku zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="a4c43-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="a4c43-107">Nazwa pliku może być kwalifikowana za pomocą ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a4c43-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="a4c43-108">Należy ująć `filename` w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="a4c43-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="a4c43-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a4c43-109">Required.</span></span> <span data-ttu-id="a4c43-110">Ścieżka tagów `filename` , które prowadzą do znacznika `name` .</span><span class="sxs-lookup"><span data-stu-id="a4c43-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="a4c43-111">Ujmij ścieżkę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="a4c43-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="a4c43-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a4c43-112">Required.</span></span> <span data-ttu-id="a4c43-113">Specyfikator Name w tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="a4c43-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="a4c43-114">`Name`ma `id` .</span><span class="sxs-lookup"><span data-stu-id="a4c43-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="a4c43-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a4c43-115">Required.</span></span> <span data-ttu-id="a4c43-116">Identyfikator tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="a4c43-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="a4c43-117">Ujmij identyfikator w znaki pojedynczego cudzysłowu (' ').</span><span class="sxs-lookup"><span data-stu-id="a4c43-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4c43-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4c43-118">Remarks</span></span>  
 <span data-ttu-id="a4c43-119">Użyj `<include>` znacznika, aby odwołać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="a4c43-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="a4c43-120">Jest to alternatywa dla umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a4c43-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="a4c43-121">Ten `<include>` tag używa zalecenia języka XML Path (XPath) w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="a4c43-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="a4c43-122">Więcej informacji o sposobach dostosowywania `<include>` użycia znajduje się w temacie <https://www.w3.org/TR/xpath> .</span><span class="sxs-lookup"><span data-stu-id="a4c43-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4c43-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4c43-123">Example</span></span>  
 <span data-ttu-id="a4c43-124">Ten przykład używa `<include>` znacznika do importowania komentarzy do dokumentacji członków z pliku o nazwie `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="a4c43-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a4c43-125">Format `commentFile.xml` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="a4c43-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4c43-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4c43-126">See also</span></span>

- [<span data-ttu-id="a4c43-127">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="a4c43-127">XML Comment Tags</span></span>](index.md)
