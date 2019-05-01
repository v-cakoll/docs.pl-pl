---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091702"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="78669-101">Metody MachineKey.Encode i MachineKey.Decode są obecnie przestarzałe</span><span class="sxs-lookup"><span data-stu-id="78669-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="78669-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="78669-102">Details</span></span>|<span data-ttu-id="78669-103">Te metody są już nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="78669-103">These methods are now obsolete.</span></span> <span data-ttu-id="78669-104">Kompilacja kodu, który wywołuje te metody, powoduje powstanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="78669-104">Compilation of code that calls these methods produces a compiler warning.</span></span>|
|<span data-ttu-id="78669-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="78669-105">Suggestion</span></span>|<span data-ttu-id="78669-106">Zalecanymi alternatywami są <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> i <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="78669-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="78669-107">Alternatywnie można pominąć ostrzeżenia kompilacji lub można uniknąć za pomocą starszego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="78669-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="78669-108">Interfejsy API są nadal obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="78669-108">The APIs are still supported.</span></span>|
|<span data-ttu-id="78669-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="78669-109">Scope</span></span>|<span data-ttu-id="78669-110">Mały</span><span class="sxs-lookup"><span data-stu-id="78669-110">Minor</span></span>|
|<span data-ttu-id="78669-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="78669-111">Version</span></span>|<span data-ttu-id="78669-112">4.5</span><span class="sxs-lookup"><span data-stu-id="78669-112">4.5</span></span>|
|<span data-ttu-id="78669-113">Typ</span><span class="sxs-lookup"><span data-stu-id="78669-113">Type</span></span>|<span data-ttu-id="78669-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="78669-114">Retargeting</span></span>|
|<span data-ttu-id="78669-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="78669-115">Affected APIs</span></span>|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
