---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620277"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="b4059-101">Karty strumienia WinRT nie są długie wywołania FlushAsync automatycznie przy zamykaniu</span><span class="sxs-lookup"><span data-stu-id="b4059-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="b4059-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b4059-102">Details</span></span>

<span data-ttu-id="b4059-103">W aplikacjach ze sklepu Windows środowisko wykonawcze systemu Windows karty usługi Stream nie wywołują już metody FlushAsync z metody Dispose.</span><span class="sxs-lookup"><span data-stu-id="b4059-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4059-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b4059-104">Suggestion</span></span>

<span data-ttu-id="b4059-105">Ta zmiana powinna być niewidoczna.</span><span class="sxs-lookup"><span data-stu-id="b4059-105">This change should be transparent.</span></span> <span data-ttu-id="b4059-106">Deweloperzy mogą przywrócić poprzednie zachowanie, pisząc kod podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="b4059-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="b4059-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b4059-107">Name</span></span>    | <span data-ttu-id="b4059-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="b4059-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4059-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="b4059-109">Scope</span></span>   |<span data-ttu-id="b4059-110">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="b4059-110">Transparent</span></span>|
|<span data-ttu-id="b4059-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="b4059-111">Version</span></span>|<span data-ttu-id="b4059-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b4059-112">4.5.1</span></span>|
|<span data-ttu-id="b4059-113">Typ</span><span class="sxs-lookup"><span data-stu-id="b4059-113">Type</span></span>|<span data-ttu-id="b4059-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b4059-114">Runtime</span></span>|
