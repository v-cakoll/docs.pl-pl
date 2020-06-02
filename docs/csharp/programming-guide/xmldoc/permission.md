---
title: <permission> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: bb7172042f0b472d03c3fa2d9dbd0d4d4265076b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287275"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="0e7fc-102">\<permission>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0e7fc-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e7fc-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e7fc-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="0e7fc-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e7fc-104">Parameters</span></span>

- <span data-ttu-id="0e7fc-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="0e7fc-105">cref = " `member`"</span></span>

  <span data-ttu-id="0e7fc-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0e7fc-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="0e7fc-107">Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="0e7fc-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="0e7fc-108">*składowa* musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="0e7fc-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="0e7fc-109">Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="0e7fc-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="0e7fc-110">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0e7fc-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e7fc-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e7fc-111">Remarks</span></span>

<span data-ttu-id="0e7fc-112">`<permission>`Tag umożliwia dokumentowanie dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0e7fc-112">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="0e7fc-113"><xref:System.Security.PermissionSet>Klasa pozwala określić dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0e7fc-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="0e7fc-114">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="0e7fc-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0e7fc-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e7fc-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="0e7fc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e7fc-116">See also</span></span>

- [<span data-ttu-id="0e7fc-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0e7fc-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0e7fc-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="0e7fc-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
