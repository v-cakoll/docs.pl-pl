---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524703"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="27738-102">> \<permission (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27738-102">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="27738-103">Określa wymagane uprawnienie dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="27738-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27738-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27738-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="27738-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27738-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="27738-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="27738-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="27738-107">Kompilator sprawdza, czy dany element kodu istnieje i tłumaczy `member` na nazwę elementu kanonicznego w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="27738-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="27738-108">Ujmij `member` w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="27738-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="27738-109">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="27738-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27738-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27738-110">Remarks</span></span>  
 <span data-ttu-id="27738-111">Użyj znacznika `<permission>`, aby udokumentować dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="27738-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="27738-112">Użyj klasy <xref:System.Security.PermissionSet>, aby określić dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="27738-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="27738-113">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="27738-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27738-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="27738-114">Example</span></span>  
 <span data-ttu-id="27738-115">W tym przykładzie używa znacznika `<permission>`, aby opisać, że <xref:System.Security.Permissions.FileIOPermission> jest wymagany przez metodę `ReadFile`.</span><span class="sxs-lookup"><span data-stu-id="27738-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="27738-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27738-116">See also</span></span>

- [<span data-ttu-id="27738-117">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="27738-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
