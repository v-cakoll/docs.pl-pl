---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858537"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="3d65a-101">Okna WPF są renderowane bez przycinania podczas rozciągania poza jednym monitorem</span><span class="sxs-lookup"><span data-stu-id="3d65a-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3d65a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3d65a-102">Details</span></span>|<span data-ttu-id="3d65a-103">W programie .NET Framework 4.6 działającym w systemie Windows 8 i wyższym całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z wieloma monitorami.</span><span class="sxs-lookup"><span data-stu-id="3d65a-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="3d65a-104">Różni się to od poprzednich wersji programu .NET Framework, które przycinałyby okna WPF, które wykraczały poza jeden ekran.</span><span class="sxs-lookup"><span data-stu-id="3d65a-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="3d65a-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3d65a-105">Suggestion</span></span>|<span data-ttu-id="3d65a-106">To zachowanie (czy do klipu lub nie) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> można <code>&lt;appSettings&gt;</code> jawnie ustawić przy użyciu elementu <code>EnableMultiMonitorDisplayClipping</code> w pliku konfiguracyjnym aplikacji lub ustawiając właściwość podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d65a-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="3d65a-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="3d65a-107">Scope</span></span>|<span data-ttu-id="3d65a-108">Mały</span><span class="sxs-lookup"><span data-stu-id="3d65a-108">Minor</span></span>|
|<span data-ttu-id="3d65a-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="3d65a-109">Version</span></span>|<span data-ttu-id="3d65a-110">4.6</span><span class="sxs-lookup"><span data-stu-id="3d65a-110">4.6</span></span>|
|<span data-ttu-id="3d65a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3d65a-111">Type</span></span>|<span data-ttu-id="3d65a-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3d65a-112">Runtime</span></span>|
