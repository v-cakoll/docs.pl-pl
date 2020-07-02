---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615657"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="7b556-101">Technologia ClickOnce obsługuje Algorytm SHA-256 w aplikacjach przeznaczonych dla 4,0</span><span class="sxs-lookup"><span data-stu-id="7b556-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="7b556-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7b556-102">Details</span></span>

<span data-ttu-id="7b556-103">Wcześniej Aplikacja ClickOnce z certyfikatem podpisanym przy użyciu algorytmu SHA-256 wymagała obecności .NET Framework 4,5 lub nowszej, nawet jeśli aplikacja skierowana do sieci 4,0.</span><span class="sxs-lookup"><span data-stu-id="7b556-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="7b556-104">Teraz aplikacje ClickOnce w .NET Framework 4,0 mogą działać na .NET Framework 4,0, nawet jeśli są podpisane przy użyciu algorytmu SHA-256.</span><span class="sxs-lookup"><span data-stu-id="7b556-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7b556-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7b556-105">Suggestion</span></span>

<span data-ttu-id="7b556-106">Ta zmiana usuwa tę zależność i zezwala na używanie certyfikatów SHA-256 do podpisywania aplikacji ClickOnce przeznaczonych dla .NET Framework 4 i wcześniejszych.</span><span class="sxs-lookup"><span data-stu-id="7b556-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="7b556-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7b556-107">Name</span></span>    | <span data-ttu-id="7b556-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="7b556-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7b556-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="7b556-109">Scope</span></span>   | <span data-ttu-id="7b556-110">Mały</span><span class="sxs-lookup"><span data-stu-id="7b556-110">Minor</span></span>       |
| <span data-ttu-id="7b556-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="7b556-111">Version</span></span> | <span data-ttu-id="7b556-112">4.6</span><span class="sxs-lookup"><span data-stu-id="7b556-112">4.6</span></span>         |
| <span data-ttu-id="7b556-113">Typ</span><span class="sxs-lookup"><span data-stu-id="7b556-113">Type</span></span>    | <span data-ttu-id="7b556-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="7b556-114">Retargeting</span></span> |
