---
title: '&lt;obejmują&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 65bc0439696612cd8331a9c0718efcfee83af574
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="eb1d3-102">&lt;obejmują&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb1d3-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="eb1d3-103">Odwołuje się do innego pliku, który opisuje typy i składniki w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb1d3-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb1d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb1d3-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="eb1d3-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-106">Required.</span></span> <span data-ttu-id="eb1d3-107">Nazwa pliku zawierającego w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="eb1d3-108">Nazwa pliku może być kwalifikowany za pomocą ścieżki.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="eb1d3-109">Umieść `filename` w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="eb1d3-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="eb1d3-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-110">Required.</span></span> <span data-ttu-id="eb1d3-111">Ścieżka tagów w `filename` prowadzi to do tagu `name`.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="eb1d3-112">Ścieżka do ujmij ją w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="eb1d3-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="eb1d3-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-113">Required.</span></span> <span data-ttu-id="eb1d3-114">Określenie nazwy w tagu poprzedzający komentarze.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="eb1d3-115">`Name` będzie mieć `id`.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="eb1d3-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-116">Required.</span></span> <span data-ttu-id="eb1d3-117">Identyfikator znacznika poprzedzający komentarze.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="eb1d3-118">Umieść identyfikator w pojedynczym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="eb1d3-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb1d3-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb1d3-119">Remarks</span></span>  
 <span data-ttu-id="eb1d3-120">Użyj `<include>` tag do odwoływania się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="eb1d3-121">Jest to alternatywa do wprowadzania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="eb1d3-122">`<include>` Tag używa zalecenie W3C XML Path Language (XPath) w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="eb1d3-123">Więcej informacji o sposobach dostosowywania Twojej `<include>` użycia znajduje się w temacie http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb1d3-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb1d3-124">Example</span></span>  
 <span data-ttu-id="eb1d3-125">W tym przykładzie użyto `<include>` tag importowanego elementu członkowskiego komentarzy do dokumentacji w pliku o nazwie `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="eb1d3-126">Format `commentFile.xml` ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="eb1d3-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb1d3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb1d3-127">See Also</span></span>  
 [<span data-ttu-id="eb1d3-128">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="eb1d3-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
