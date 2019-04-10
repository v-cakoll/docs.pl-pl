---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234796"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="c4213-101">Metody MachineKey.Encode i MachineKey.Decode są obecnie przestarzałe</span><span class="sxs-lookup"><span data-stu-id="c4213-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c4213-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c4213-102">Details</span></span>|<span data-ttu-id="c4213-103">Te metody są już nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="c4213-103">These methods are now obsolete.</span></span> <span data-ttu-id="c4213-104">Kompilacja kodu, który wywołuje te metody, powoduje powstanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c4213-104">Compilation of code that calls these methods produces a compiler warning.</span></span>|
|<span data-ttu-id="c4213-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c4213-105">Suggestion</span></span>|<span data-ttu-id="c4213-106">Zalecanymi alternatywami są <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> i <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="c4213-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="c4213-107">Alternatywnie można pominąć ostrzeżenia kompilacji lub można uniknąć za pomocą starszego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c4213-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="c4213-108">Interfejsy API są nadal obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c4213-108">The APIs are still supported.</span></span>|
|<span data-ttu-id="c4213-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="c4213-109">Scope</span></span>|<span data-ttu-id="c4213-110">Mały</span><span class="sxs-lookup"><span data-stu-id="c4213-110">Minor</span></span>|
|<span data-ttu-id="c4213-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="c4213-111">Version</span></span>|<span data-ttu-id="c4213-112">4.5</span><span class="sxs-lookup"><span data-stu-id="c4213-112">4.5</span></span>|
|<span data-ttu-id="c4213-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c4213-113">Type</span></span>|<span data-ttu-id="c4213-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="c4213-114">Retargeting</span></span>|
|<span data-ttu-id="c4213-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c4213-115">Affected APIs</span></span>|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
