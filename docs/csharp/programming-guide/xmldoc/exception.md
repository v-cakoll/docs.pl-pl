---
title: "&lt;wyjątek&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd859a09bfbe9f814bf57f0987fd49ded9ba7100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="8fdfa-102">&lt;wyjątek&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="8fdfa-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="8fdfa-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fdfa-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fdfa-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fdfa-104">Parameters</span></span>  
 <span data-ttu-id="8fdfa-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="8fdfa-105">cref = " `member`"</span></span>  
 <span data-ttu-id="8fdfa-106">Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8fdfa-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="8fdfa-107">Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element wyjściowy element XML.</span><span class="sxs-lookup"><span data-stu-id="8fdfa-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="8fdfa-108">`member`musi występować w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="8fdfa-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="8fdfa-109">Aby uzyskać więcej informacji na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="8fdfa-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="8fdfa-110">Opis wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8fdfa-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fdfa-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fdfa-111">Remarks</span></span>  
 <span data-ttu-id="8fdfa-112">\<Wyjątku > należy określić, które wyjątki może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="8fdfa-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="8fdfa-113">Ten tag może odnosić się do definicji dla metod, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="8fdfa-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="8fdfa-114">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="8fdfa-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="8fdfa-115">Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="8fdfa-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fdfa-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fdfa-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8fdfa-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fdfa-117">See Also</span></span>  
 [<span data-ttu-id="8fdfa-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8fdfa-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8fdfa-119">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="8fdfa-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
