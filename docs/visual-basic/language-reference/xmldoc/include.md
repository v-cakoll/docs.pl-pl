---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348463"
---
# <a name="include-visual-basic"></a><span data-ttu-id="f5304-101">\<Uwzględnij > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5304-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="f5304-102">Odwołuje się do innego pliku opisującego typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f5304-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5304-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5304-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5304-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5304-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="f5304-105">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5304-105">Required.</span></span> <span data-ttu-id="f5304-106">Nazwa pliku zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="f5304-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="f5304-107">Nazwa pliku może być kwalifikowana za pomocą ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f5304-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="f5304-108">Ujmij `filename` w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="f5304-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="f5304-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5304-109">Required.</span></span> <span data-ttu-id="f5304-110">Ścieżka tagów w `filename`, które prowadzą do `name`znacznika.</span><span class="sxs-lookup"><span data-stu-id="f5304-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="f5304-111">Ujmij ścieżkę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="f5304-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="f5304-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5304-112">Required.</span></span> <span data-ttu-id="f5304-113">Specyfikator Name w tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="f5304-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="f5304-114">`Name` będzie `id`.</span><span class="sxs-lookup"><span data-stu-id="f5304-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="f5304-115">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f5304-115">Required.</span></span> <span data-ttu-id="f5304-116">Identyfikator tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="f5304-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="f5304-117">Ujmij identyfikator w znaki pojedynczego cudzysłowu (' ').</span><span class="sxs-lookup"><span data-stu-id="f5304-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5304-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5304-118">Remarks</span></span>  
 <span data-ttu-id="f5304-119">Użyj znacznika `<include>`, aby odwołać się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="f5304-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="f5304-120">Jest to alternatywa dla umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f5304-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="f5304-121">Tag `<include>` używa zalecenia XML (W3C) Path Language (XPath) w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="f5304-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="f5304-122">Aby uzyskać więcej informacji o sposobach dostosowywania użycia `<include>`, zobacz <https://www.w3.org/TR/xpath>.</span><span class="sxs-lookup"><span data-stu-id="f5304-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5304-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5304-123">Example</span></span>  
 <span data-ttu-id="f5304-124">W tym przykładzie używa znacznika `<include>` do importowania komentarzy do dokumentacji członków z pliku o nazwie `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="f5304-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f5304-125">Format `commentFile.xml` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="f5304-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5304-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5304-126">See also</span></span>

- [<span data-ttu-id="f5304-127">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="f5304-127">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
