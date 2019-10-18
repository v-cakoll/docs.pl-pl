---
title: <exception> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 4e4204996c006ce6e943c9a09661001b0e0c2a14
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523474"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="fb4d4-102">\<exception > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="fb4d4-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fb4d4-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb4d4-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb4d4-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb4d4-104">Parameters</span></span>  
 <span data-ttu-id="fb4d4-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="fb4d4-105">cref = " `member`"</span></span>  
 <span data-ttu-id="fb4d4-106">Odwołanie do wyjątku, które jest dostępne w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fb4d4-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="fb4d4-107">Kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="fb4d4-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="fb4d4-108">`member` musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="fb4d4-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="fb4d4-109">Aby uzyskać więcej informacji na temat sposobu formatowania `member` w celu odwoływania się do typu ogólnego, zobacz [przetwarzanie pliku XML](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="fb4d4-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>
  
 `description`  
 <span data-ttu-id="fb4d4-110">Opis wyjątku.</span><span class="sxs-lookup"><span data-stu-id="fb4d4-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb4d4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb4d4-111">Remarks</span></span>  
 <span data-ttu-id="fb4d4-112">Tag \<exception > pozwala określić, które wyjątki mogą być zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="fb4d4-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="fb4d4-113">Ten tag można zastosować do definicji metod, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="fb4d4-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="fb4d4-114">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="fb4d4-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="fb4d4-115">Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki i obsługa wyjątków](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb4d4-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb4d4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb4d4-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fb4d4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb4d4-117">See also</span></span>

- [<span data-ttu-id="fb4d4-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fb4d4-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fb4d4-119">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="fb4d4-119">Recommended Tags for Documentation Comments</span></span>](recommended-tags-for-documentation-comments.md)
