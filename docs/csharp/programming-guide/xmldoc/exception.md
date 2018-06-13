---
title: '&lt;wyjątek&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: eca61416077896c9fa7d5828bbab79b399ad69d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332663"
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="6d7a1-102">&lt;wyjątek&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="6d7a1-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6d7a1-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d7a1-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d7a1-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d7a1-104">Parameters</span></span>  
 <span data-ttu-id="6d7a1-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="6d7a1-105">cref = " `member`"</span></span>  
 <span data-ttu-id="6d7a1-106">Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="6d7a1-107">Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element wyjściowy element XML.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="6d7a1-108">`member` musi występować w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="6d7a1-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="6d7a1-109">Aby uzyskać więcej informacji na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="6d7a1-110">Opis wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d7a1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d7a1-111">Remarks</span></span>  
 <span data-ttu-id="6d7a1-112">\<Wyjątku > należy określić, które wyjątki może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="6d7a1-113">Ten tag może odnosić się do definicji dla metod, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="6d7a1-114">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="6d7a1-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="6d7a1-115">Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d7a1-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7a1-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d7a1-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d7a1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d7a1-117">See Also</span></span>  
 [<span data-ttu-id="6d7a1-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6d7a1-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d7a1-119">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="6d7a1-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
