---
title: <permission> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 475e9ab5c59260544b0e413e165953c0b84449b5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973902"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="729a8-102">\<uprawnienie > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="729a8-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="729a8-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="729a8-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="729a8-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="729a8-104">Parameters</span></span>  
 <span data-ttu-id="729a8-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="729a8-105">cref = " `member`"</span></span>  
 <span data-ttu-id="729a8-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="729a8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="729a8-107">Kompilator sprawdza, czy dany element kodu istnieje i wykonuje translację `member` nazwę kanoniczną element w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="729a8-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="729a8-108">*element członkowski* musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="729a8-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="729a8-109">Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="729a8-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="729a8-110">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="729a8-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="729a8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="729a8-111">Remarks</span></span>  
 <span data-ttu-id="729a8-112">\<Uprawnienia > znacznik umożliwia dokumentowanie dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="729a8-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="729a8-113"><xref:System.Security.PermissionSet> Klasy pozwala określić dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="729a8-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="729a8-114">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="729a8-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="729a8-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="729a8-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="729a8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="729a8-116">See also</span></span>

- [<span data-ttu-id="729a8-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="729a8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="729a8-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="729a8-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
