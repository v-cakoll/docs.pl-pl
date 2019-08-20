---
title: <seealso> — C# Przewodnik programowania
ms.custom: seodec18
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
ms.openlocfilehash: 3ddaa7efec2b4bf5ffa53971aa6f380a1be9bad8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587656"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="79950-102">\<seealso — > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="79950-102">\<seealso> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="79950-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="79950-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="79950-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="79950-104">Parameters</span></span>  
 <span data-ttu-id="79950-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="79950-105">cref = " `member`"</span></span>  
 <span data-ttu-id="79950-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="79950-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="79950-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.`member`</span><span class="sxs-lookup"><span data-stu-id="79950-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="79950-108">musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="79950-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="79950-109">Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [ \<temat >](./see.md).</span><span class="sxs-lookup"><span data-stu-id="79950-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79950-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79950-110">Remarks</span></span>  
 <span data-ttu-id="79950-111">Tag \<> seealso — umożliwia określenie tekstu, który może być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="79950-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="79950-112">Użyj >, aby określić łącze z tekstu. [ \<](./see.md)</span><span class="sxs-lookup"><span data-stu-id="79950-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="79950-113">Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="79950-113">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79950-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="79950-114">Example</span></span>  
 <span data-ttu-id="79950-115">\< [ Zobacz\<> podsumowujące](./summary.md) , aby zapoznać się z przykładem użycia usługi seealso — >.</span><span class="sxs-lookup"><span data-stu-id="79950-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79950-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79950-116">See also</span></span>

- [<span data-ttu-id="79950-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="79950-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="79950-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="79950-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
