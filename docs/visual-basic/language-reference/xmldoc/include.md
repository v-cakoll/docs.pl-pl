---
title: '&lt;obejmują&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: da7a6c15c558fc56dbc6a874d4a28c4434f67668
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455976"
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="2685c-102">&lt;obejmują&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2685c-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="2685c-103">Odnosi się do innego pliku, który opisuje typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="2685c-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2685c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2685c-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2685c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2685c-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="2685c-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2685c-106">Required.</span></span> <span data-ttu-id="2685c-107">Nazwa pliku zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="2685c-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="2685c-108">Nazwa pliku może być kwalifikowana przy użyciu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2685c-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="2685c-109">Ujmij `filename` w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="2685c-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="2685c-110">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2685c-110">Required.</span></span> <span data-ttu-id="2685c-111">Ścieżka znaczniki `filename` prowadzi to do tagu `name`.</span><span class="sxs-lookup"><span data-stu-id="2685c-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="2685c-112">Zamknij ścieżkę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="2685c-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="2685c-113">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2685c-113">Required.</span></span> <span data-ttu-id="2685c-114">Określenie nazwy w tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="2685c-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="2685c-115">`Name` będzie miał `id`.</span><span class="sxs-lookup"><span data-stu-id="2685c-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="2685c-116">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2685c-116">Required.</span></span> <span data-ttu-id="2685c-117">Identyfikator tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="2685c-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="2685c-118">Umieść identyfikator w znaki pojedynczego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="2685c-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2685c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2685c-119">Remarks</span></span>  
 <span data-ttu-id="2685c-120">Użyj `<include>` tag do odwoływania się do komentarzy w innym pliku, które opisują typy i elementy członkowskie w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="2685c-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="2685c-121">Jest to alternatywa do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2685c-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="2685c-122">`<include>` Tag używa zalecenie w wersji 1.0 W3C XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="2685c-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="2685c-123">Więcej informacji o sposobach dostosowywania swoje `<include>` użycia znajduje się w temacie http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="2685c-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2685c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2685c-124">Example</span></span>  
 <span data-ttu-id="2685c-125">W tym przykładzie użyto `<include>` tag, aby zaimportować komentarzy dokumentacji elementu członkowskiego z pliku o nazwie `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="2685c-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="2685c-126">Format `commentFile.xml` jest następujący.</span><span class="sxs-lookup"><span data-stu-id="2685c-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2685c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2685c-127">See Also</span></span>  
 [<span data-ttu-id="2685c-128">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="2685c-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
