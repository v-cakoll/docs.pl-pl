---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616074"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="b55a2-101">VB.NET nie obsługuje już częściowego kwalifikowania przestrzeni nazw dla interfejsów API System. Windows</span><span class="sxs-lookup"><span data-stu-id="b55a2-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="b55a2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b55a2-102">Details</span></span>

<span data-ttu-id="b55a2-103">Począwszy od .NET Framework 4.5.2, projekty VB.NET nie mogą określać interfejsów API System. Windows z częściowo kwalifikowanymi przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="b55a2-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="b55a2-104">Na przykład odwołanie do `Windows.Forms.DialogResult` nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="b55a2-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="b55a2-105">Zamiast tego, kod musi odwoływać się do w pełni kwalifikowanej nazwy ( <xref:System.Windows.Forms.DialogResult> ) lub zaimportować określoną przestrzeń nazw i zajrzeć się po prostu do <xref:System.Windows.Forms.DialogResult?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="b55a2-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b55a2-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b55a2-106">Suggestion</span></span>

<span data-ttu-id="b55a2-107">Kod powinien zostać zaktualizowany w celu odwoływania się do `System.Windows` interfejsów API przy użyciu prostych nazw (i importowania odpowiedniej przestrzeni nazw) lub z w pełni kwalifikowanymi nazwami.</span><span class="sxs-lookup"><span data-stu-id="b55a2-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="b55a2-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b55a2-108">Name</span></span>    | <span data-ttu-id="b55a2-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="b55a2-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b55a2-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="b55a2-110">Scope</span></span>   | <span data-ttu-id="b55a2-111">Mały</span><span class="sxs-lookup"><span data-stu-id="b55a2-111">Minor</span></span>       |
| <span data-ttu-id="b55a2-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="b55a2-112">Version</span></span> | <span data-ttu-id="b55a2-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="b55a2-113">4.5.2</span></span>       |
| <span data-ttu-id="b55a2-114">Typ</span><span class="sxs-lookup"><span data-stu-id="b55a2-114">Type</span></span>    | <span data-ttu-id="b55a2-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="b55a2-115">Retargeting</span></span> |
