---
title: '&lt;SeeAlso&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e3c9d68884e5cd4f5a4f81580f60cdde775458a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349138"
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="1ffdb-102">&lt;SeeAlso&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1ffdb-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ffdb-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ffdb-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ffdb-104">Parameters</span></span>  
 <span data-ttu-id="1ffdb-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="1ffdb-105">cref = " `member`"</span></span>  
 <span data-ttu-id="1ffdb-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="1ffdb-107">Kompilator sprawdza, czy element podanego kodu istnieje i przekazuje `member` do nazwy elementu w danych wyjściowych XML.`member`</span><span class="sxs-lookup"><span data-stu-id="1ffdb-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="1ffdb-108">musi występować w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="1ffdb-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="1ffdb-109">Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="1ffdb-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ffdb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ffdb-110">Remarks</span></span>  
 <span data-ttu-id="1ffdb-111">\<Seealso > należy określić tekst, który ma być wyświetlane w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="1ffdb-112">Użyj [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md) można określić łącze od w tekście.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="1ffdb-113">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ffdb-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ffdb-114">Example</span></span>  
 <span data-ttu-id="1ffdb-115">Zobacz [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) przykład za pomocą \<seealso >.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffdb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ffdb-116">See Also</span></span>  
 [<span data-ttu-id="1ffdb-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1ffdb-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1ffdb-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="1ffdb-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
