---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621358"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="b2db3-101">Okna WPF są renderowane bez obcinania podczas rozszerzania poza pojedynczy monitor</span><span class="sxs-lookup"><span data-stu-id="b2db3-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="b2db3-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b2db3-102">Details</span></span>

<span data-ttu-id="b2db3-103">W .NET Framework 4,6 działający w systemie Windows 8 i nowszych całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z obsługą kilku monitorów.</span><span class="sxs-lookup"><span data-stu-id="b2db3-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="b2db3-104">Różni się to od poprzednich wersji .NET Framework, które powinny wyciąć okna WPF, które przekroczą pojedynczy ekran.</span><span class="sxs-lookup"><span data-stu-id="b2db3-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b2db3-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b2db3-105">Suggestion</span></span>

<span data-ttu-id="b2db3-106">Takie zachowanie (bez względu na to, czy ma być obcinane czy nie) można jawnie ustawić przy użyciu <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> elementu w <code>&lt;appSettings&gt;</code> pliku konfiguracyjnym aplikacji lub przez ustawienie <code>EnableMultiMonitorDisplayClipping</code> właściwości przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2db3-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="b2db3-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b2db3-107">Name</span></span>    | <span data-ttu-id="b2db3-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="b2db3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b2db3-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="b2db3-109">Scope</span></span>   |<span data-ttu-id="b2db3-110">Mały</span><span class="sxs-lookup"><span data-stu-id="b2db3-110">Minor</span></span>|
|<span data-ttu-id="b2db3-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="b2db3-111">Version</span></span>|<span data-ttu-id="b2db3-112">4.6</span><span class="sxs-lookup"><span data-stu-id="b2db3-112">4.6</span></span>|
|<span data-ttu-id="b2db3-113">Typ</span><span class="sxs-lookup"><span data-stu-id="b2db3-113">Type</span></span>|<span data-ttu-id="b2db3-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b2db3-114">Runtime</span></span>|
