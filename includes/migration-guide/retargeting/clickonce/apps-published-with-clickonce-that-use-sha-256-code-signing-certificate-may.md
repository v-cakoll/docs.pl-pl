---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615659"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="08ad4-101">Aplikacje opublikowane przy użyciu technologii ClickOnce wykorzystującej certyfikat podpisywania kodu SHA-256 mogą kończyć się niepowodzeniem w systemie Windows 2003</span><span class="sxs-lookup"><span data-stu-id="08ad4-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="08ad4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="08ad4-102">Details</span></span>

<span data-ttu-id="08ad4-103">Plik wykonywalny jest podpisany za pomocą SHA256.</span><span class="sxs-lookup"><span data-stu-id="08ad4-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="08ad4-104">Wcześniej było podpisane przy użyciu algorytmu SHA1, niezależnie od tego, czy certyfikat podpisywania kodu był algorytmem SHA-1 lub SHA-256.</span><span class="sxs-lookup"><span data-stu-id="08ad4-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="08ad4-105">Dotyczy to:</span><span class="sxs-lookup"><span data-stu-id="08ad4-105">This applies to:</span></span>

- <span data-ttu-id="08ad4-106">Wszystkie aplikacje skompilowane przy użyciu programu Visual Studio 2012 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="08ad4-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="08ad4-107">Aplikacje skompilowane przy użyciu programu Visual Studio 2010 lub starszej wersji w systemach z .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="08ad4-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="08ad4-108">Ponadto jeśli jest obecny .NET Framework 4,5 lub nowszy, manifest ClickOnce jest również podpisany przy użyciu algorytmu SHA-256 dla certyfikatów SHA-256 niezależnie od wersji .NET Framework, z którą została skompilowana.</span><span class="sxs-lookup"><span data-stu-id="08ad4-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="08ad4-109">Sugestia</span><span class="sxs-lookup"><span data-stu-id="08ad4-109">Suggestion</span></span>

<span data-ttu-id="08ad4-110">Zmiana podczas podpisywania pliku wykonywalnego ClickOnce dotyczy tylko systemów Windows Server 2003; wymagają one zainstalowania KB 938397.</span><span class="sxs-lookup"><span data-stu-id="08ad4-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="08ad4-111">Zmiana podczas podpisywania manifestu z algorytmem SHA-256 nawet wtedy, gdy aplikacja jest przeznaczona dla .NET Framework 4,0 lub wcześniejszych wersji wprowadza zależność środowiska uruchomieniowego na .NET Framework 4,5 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="08ad4-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="08ad4-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="08ad4-112">Name</span></span>    | <span data-ttu-id="08ad4-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="08ad4-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="08ad4-114">Zakres</span><span class="sxs-lookup"><span data-stu-id="08ad4-114">Scope</span></span>   | <span data-ttu-id="08ad4-115">Brzeg</span><span class="sxs-lookup"><span data-stu-id="08ad4-115">Edge</span></span>        |
| <span data-ttu-id="08ad4-116">Wersja</span><span class="sxs-lookup"><span data-stu-id="08ad4-116">Version</span></span> | <span data-ttu-id="08ad4-117">4.5</span><span class="sxs-lookup"><span data-stu-id="08ad4-117">4.5</span></span>         |
| <span data-ttu-id="08ad4-118">Typ</span><span class="sxs-lookup"><span data-stu-id="08ad4-118">Type</span></span>    | <span data-ttu-id="08ad4-119">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="08ad4-119">Retargeting</span></span> |
