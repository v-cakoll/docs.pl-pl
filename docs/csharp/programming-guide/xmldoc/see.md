---
title: <see> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 31806ad06cc97fa27f1944f2500f0f9cbb29f561
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262104"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="b534c-102">\<zobacz > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b534c-102">\<see> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b534c-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="b534c-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b534c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b534c-104">Parameters</span></span>  
 <span data-ttu-id="b534c-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="b534c-105">cref = " `member`"</span></span>  
 <span data-ttu-id="b534c-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b534c-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="b534c-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="b534c-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="b534c-108">Miejsce *elementu członkowskiego* w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="b534c-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b534c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b534c-109">Remarks</span></span>  
 <span data-ttu-id="b534c-110">\<Zobacz > należy określić łącze między w tekście.</span><span class="sxs-lookup"><span data-stu-id="b534c-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="b534c-111">Użyj [ \<SeeAlso — >](../../../csharp/programming-guide/xmldoc/seealso.md) do wskazania, że tekst powinny być umieszczone w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="b534c-111">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="b534c-112">Użyj [cref — atrybut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) do utworzenia wewnętrznego hiperlinki do stron dokumentacji dla elementów kodu.</span><span class="sxs-lookup"><span data-stu-id="b534c-112">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="b534c-113">Kompiluj przy użyciu [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b534c-113">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="b534c-114">W poniższym przykładzie przedstawiono \<zobacz > tagu w sekcji podsumowania.</span><span class="sxs-lookup"><span data-stu-id="b534c-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b534c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b534c-115">See also</span></span>

- [<span data-ttu-id="b534c-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b534c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b534c-117">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="b534c-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
