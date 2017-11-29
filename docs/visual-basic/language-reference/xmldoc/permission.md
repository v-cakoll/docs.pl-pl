---
title: '&lt;uprawnienie&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67e11998e43a43f92c26eb5f7daa488d288823c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="cca3d-102">&lt;uprawnienie&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca3d-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="cca3d-103">Określa uprawnienia wymagane dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cca3d-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cca3d-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cca3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cca3d-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="cca3d-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cca3d-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cca3d-107">Kompilator sprawdza, czy element podanego kodu istnieje i wykonuje translację `member` nazwę kanoniczną element wyjściowy element XML.</span><span class="sxs-lookup"><span data-stu-id="cca3d-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="cca3d-108">Umieść `member` w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="cca3d-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="cca3d-109">Opis dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cca3d-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cca3d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cca3d-110">Remarks</span></span>  
 <span data-ttu-id="cca3d-111">Użyj `<permission>` tag dokumentów dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cca3d-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="cca3d-112">Użyj <xref:System.Security.PermissionSet> klasę, aby określić dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cca3d-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="cca3d-113">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="cca3d-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cca3d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="cca3d-114">Example</span></span>  
 <span data-ttu-id="cca3d-115">W tym przykładzie użyto `<permission>` tag, aby przedstawić <xref:System.Security.Permissions.FileIOPermission> jest wymagany przez `ReadFile` metody.</span><span class="sxs-lookup"><span data-stu-id="cca3d-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cca3d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cca3d-116">See Also</span></span>  
 [<span data-ttu-id="cca3d-117">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="cca3d-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
