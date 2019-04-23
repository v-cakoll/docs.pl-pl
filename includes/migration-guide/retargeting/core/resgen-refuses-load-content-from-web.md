---
ms.openlocfilehash: 6cdd410cc818c2c0a993a364e550f5f92ed6a821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981847"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="15fa5-101">ResGen odmawia do załadowania zawartości z sieci web</span><span class="sxs-lookup"><span data-stu-id="15fa5-101">Resgen refuses to load content from the web</span></span>

|   |   |
|---|---|
|<span data-ttu-id="15fa5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="15fa5-102">Details</span></span>|<span data-ttu-id="15fa5-103">pliki resx mogą zawierać binarne sformatowane dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="15fa5-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="15fa5-104">Jeśli spróbujesz użyć resgen można załadować pliku, który został pobrany z lokalizacji niezaufanych, zakończy się niepowodzeniem do ładowania danych wejściowych domyślnie.</span><span class="sxs-lookup"><span data-stu-id="15fa5-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>|
|<span data-ttu-id="15fa5-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="15fa5-105">Suggestion</span></span>|<span data-ttu-id="15fa5-106">ResGen użytkowników, którzy potrzebują ładowanie binarne sformatowane dane wejściowe z niezaufanych lokalizacji można usunąć znacznik sieci Web z pliku wejściowego lub niedoskonałość rezygnacji z zastosowania. Dodaj następujące ustawienie rejestru, aby zastosować niedoskonałość szeroki rezygnacji maszyny: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span><span class="sxs-lookup"><span data-stu-id="15fa5-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>|
|<span data-ttu-id="15fa5-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="15fa5-107">Scope</span></span>|<span data-ttu-id="15fa5-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="15fa5-108">Edge</span></span>|
|<span data-ttu-id="15fa5-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="15fa5-109">Version</span></span>|<span data-ttu-id="15fa5-110">4.7.2</span><span class="sxs-lookup"><span data-stu-id="15fa5-110">4.7.2</span></span>|
|<span data-ttu-id="15fa5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="15fa5-111">Type</span></span>|<span data-ttu-id="15fa5-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="15fa5-112">Retargeting</span></span>|
