---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617182"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="f1935-101">Metody MachineKey. Encode i MachineKey. Decode są obecnie przestarzałe</span><span class="sxs-lookup"><span data-stu-id="f1935-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="f1935-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f1935-102">Details</span></span>

<span data-ttu-id="f1935-103">Te metody są już nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="f1935-103">These methods are now obsolete.</span></span> <span data-ttu-id="f1935-104">Kompilacja kodu, który wywołuje te metody, powoduje powstanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f1935-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f1935-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f1935-105">Suggestion</span></span>

<span data-ttu-id="f1935-106">Zalecane alternatywy to <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> i <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="f1935-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="f1935-107">Alternatywnie można pominąć ostrzeżenia kompilacji lub uniknąć ich przy użyciu starszego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f1935-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="f1935-108">Interfejsy API są nadal obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f1935-108">The APIs are still supported.</span></span>

| <span data-ttu-id="f1935-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f1935-109">Name</span></span>    | <span data-ttu-id="f1935-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="f1935-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f1935-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="f1935-111">Scope</span></span>   | <span data-ttu-id="f1935-112">Mały</span><span class="sxs-lookup"><span data-stu-id="f1935-112">Minor</span></span>       |
| <span data-ttu-id="f1935-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="f1935-113">Version</span></span> | <span data-ttu-id="f1935-114">4.5</span><span class="sxs-lookup"><span data-stu-id="f1935-114">4.5</span></span>         |
| <span data-ttu-id="f1935-115">Typ</span><span class="sxs-lookup"><span data-stu-id="f1935-115">Type</span></span>    | <span data-ttu-id="f1935-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f1935-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f1935-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f1935-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
