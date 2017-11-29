---
title: "&lt;uprawnienie&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37bb37ea14edc1f91225f9b04b18b354d99579b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="286d8-102">&lt;uprawnienie&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="286d8-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="286d8-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="286d8-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="286d8-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="286d8-104">Parameters</span></span>  
 <span data-ttu-id="286d8-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="286d8-105">cref = " `member`"</span></span>  
 <span data-ttu-id="286d8-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="286d8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="286d8-107">Kompilator sprawdza, czy element podanego kodu istnieje i wykonuje translację `member` nazwę kanoniczną element wyjściowy element XML.</span><span class="sxs-lookup"><span data-stu-id="286d8-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="286d8-108">*element członkowski* musi występować w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="286d8-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="286d8-109">Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="286d8-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="286d8-110">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="286d8-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="286d8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="286d8-111">Remarks</span></span>  
 <span data-ttu-id="286d8-112">\<Uprawnienia > znacznik umożliwia dostęp do elementu członkowskiego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="286d8-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="286d8-113"><xref:System.Security.PermissionSet> Klasa umożliwia określenie dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="286d8-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="286d8-114">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="286d8-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="286d8-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="286d8-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="286d8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="286d8-116">See Also</span></span>  
 [<span data-ttu-id="286d8-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="286d8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="286d8-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="286d8-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
