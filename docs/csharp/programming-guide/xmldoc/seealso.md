---
title: <seealso> — C# Przewodnik programowania
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093464"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="cd881-102">\<seealso — > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="cd881-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd881-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd881-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="cd881-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd881-104">Parameters</span></span>

- <span data-ttu-id="cd881-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="cd881-105">cref = " `member`"</span></span>

  <span data-ttu-id="cd881-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cd881-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cd881-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.`member`</span><span class="sxs-lookup"><span data-stu-id="cd881-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="cd881-108">musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="cd881-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="cd881-109">Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="cd881-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="cd881-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd881-110">Remarks</span></span>

<span data-ttu-id="cd881-111">Tag \<seealso — > umożliwia określenie tekstu, który ma być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="cd881-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="cd881-112">Użyj [\<zobacz >](./see.md) , aby określić łącze z tekstu.</span><span class="sxs-lookup"><span data-stu-id="cd881-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="cd881-113">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="cd881-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="cd881-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd881-114">Example</span></span>

<span data-ttu-id="cd881-115">Zobacz [\<podsumowanie >](./summary.md) , aby uzyskać przykład użycia \<seealso — >.</span><span class="sxs-lookup"><span data-stu-id="cd881-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd881-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd881-116">See also</span></span>

- [<span data-ttu-id="cd881-117">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="cd881-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="cd881-118">Zalecane Tagi dla komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="cd881-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
