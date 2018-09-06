---
title: '&lt;zobacz&gt; (C# Programming Guide)'
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
ms.openlocfilehash: c37ad869b3eb904377cd4470a85cd557f6560290
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737790"
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="1c501-102">&lt;zobacz&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="1c501-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1c501-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c501-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c501-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c501-104">Parameters</span></span>  
 <span data-ttu-id="1c501-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="1c501-105">cref = " `member`"</span></span>  
 <span data-ttu-id="1c501-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1c501-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1c501-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML. Miejsce *elementu członkowskiego* w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="1c501-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c501-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c501-108">Remarks</span></span>  
 <span data-ttu-id="1c501-109">\<Zobacz > należy określić łącze między w tekście.</span><span class="sxs-lookup"><span data-stu-id="1c501-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="1c501-110">Użyj [ \<SeeAlso — >](../../../csharp/programming-guide/xmldoc/seealso.md) do wskazania, że tekst powinny być umieszczone w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="1c501-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="1c501-111">Użyj [cref — atrybut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) do utworzenia wewnętrznego hiperlinki do stron dokumentacji dla elementów kodu.</span><span class="sxs-lookup"><span data-stu-id="1c501-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="1c501-112">Kompiluj przy użyciu [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="1c501-112">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="1c501-113">W poniższym przykładzie przedstawiono \<zobacz > tagu w sekcji podsumowania.</span><span class="sxs-lookup"><span data-stu-id="1c501-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1c501-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c501-114">See Also</span></span>

- [<span data-ttu-id="1c501-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1c501-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1c501-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="1c501-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
