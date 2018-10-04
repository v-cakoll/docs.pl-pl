---
title: '&lt;uprawnienie&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: bcec5d968f5d0c5400c28e772df151b164888a47
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793204"
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="cccb8-102">&lt;uprawnienie&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cccb8-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="cccb8-103">Określa wymagane uprawnienia dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cccb8-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cccb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cccb8-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cccb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cccb8-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="cccb8-106">Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cccb8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cccb8-107">Kompilator sprawdza, czy dany element kodu istnieje i wykonuje translację `member` nazwę kanoniczną element w danych wyjściowych XML.</span><span class="sxs-lookup"><span data-stu-id="cccb8-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="cccb8-108">Ujmij `member` w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="cccb8-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="cccb8-109">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cccb8-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cccb8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cccb8-110">Remarks</span></span>  
 <span data-ttu-id="cccb8-111">Użyj `<permission>` tag do dokumentu jest dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cccb8-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="cccb8-112">Użyj <xref:System.Security.PermissionSet> klasy w celu określenia dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cccb8-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="cccb8-113">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="cccb8-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cccb8-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cccb8-114">Example</span></span>  
 <span data-ttu-id="cccb8-115">W tym przykładzie użyto `<permission>` tag do opisywania, które <xref:System.Security.Permissions.FileIOPermission> jest wymagana przez `ReadFile` metody.</span><span class="sxs-lookup"><span data-stu-id="cccb8-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cccb8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cccb8-116">See Also</span></span>  
 [<span data-ttu-id="cccb8-117">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="cccb8-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
