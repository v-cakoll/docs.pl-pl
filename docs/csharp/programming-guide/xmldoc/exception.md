---
title: <exception> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: b316927c5dfd5eda05bea653f9a601cca9865af3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982066"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="e63fb-102">\<wyjątek > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e63fb-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e63fb-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e63fb-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e63fb-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e63fb-104">Parameters</span></span>  
 <span data-ttu-id="e63fb-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="e63fb-105">cref = " `member`"</span></span>  
 <span data-ttu-id="e63fb-106">Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e63fb-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="e63fb-107">Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="e63fb-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="e63fb-108">`member` musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="e63fb-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="e63fb-109">Aby uzyskać więcej informacji na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="e63fb-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="e63fb-110">Opis wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e63fb-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e63fb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e63fb-111">Remarks</span></span>  
 <span data-ttu-id="e63fb-112">\<Wyjątku > należy określić, które wyjątki mogą zostać wygenerowane.</span><span class="sxs-lookup"><span data-stu-id="e63fb-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="e63fb-113">Ten tag można zastosować do definicji dla metody, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="e63fb-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="e63fb-114">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e63fb-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="e63fb-115">Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątków i wyjątków](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="e63fb-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e63fb-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="e63fb-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e63fb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e63fb-117">See also</span></span>

- [<span data-ttu-id="e63fb-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e63fb-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e63fb-119">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e63fb-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
