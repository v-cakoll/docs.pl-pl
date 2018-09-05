---
title: '&lt;uprawnienie&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 1447541f7e093a7cf434702368bdce0d07c4908b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558592"
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="9c3b4-102">&lt;uprawnienie&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="9c3b4-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9c3b4-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c3b4-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c3b4-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c3b4-104">Parameters</span></span>  
 <span data-ttu-id="9c3b4-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="9c3b4-105">cref = " `member`"</span></span>  
 <span data-ttu-id="9c3b4-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c3b4-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9c3b4-107">Kompilator sprawdza, czy dany element kodu istnieje i wykonuje translację `member` nazwę kanoniczną element w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="9c3b4-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="9c3b4-108">*element członkowski* musi znajdować się w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="9c3b4-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="9c3b4-109">Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="9c3b4-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="9c3b4-110">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9c3b4-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c3b4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c3b4-111">Remarks</span></span>  
 <span data-ttu-id="9c3b4-112">\<Uprawnienia > znacznik umożliwia dokumentowanie dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9c3b4-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="9c3b4-113"><xref:System.Security.PermissionSet> Klasy pozwala określić dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9c3b4-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="9c3b4-114">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="9c3b4-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c3b4-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c3b4-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9c3b4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c3b4-116">See Also</span></span>

- [<span data-ttu-id="9c3b4-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9c3b4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9c3b4-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="9c3b4-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
