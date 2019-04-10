---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235588"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="8d830-101">WebUtility.HtmlDecode dekoduje już nieprawidłowych sekwencji wejściowych</span><span class="sxs-lookup"><span data-stu-id="8d830-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8d830-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8d830-102">Details</span></span>|<span data-ttu-id="8d830-103">Domyślnie metody dekodowania nie dekodują już nieprawidłowych sekwencji wejściowych na nieprawidłowy ciąg UTF-16.</span><span class="sxs-lookup"><span data-stu-id="8d830-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="8d830-104">Zamiast tego zwracają oryginalne dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="8d830-104">Instead, they return the original input.</span></span>|
|<span data-ttu-id="8d830-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8d830-105">Suggestion</span></span>|<span data-ttu-id="8d830-106">Zmiana w danych wyjściowych dekodera powinna mieć znaczenie tylko wtedy, gdy w ciągach zamiast danych UTF-16 są przechowywane dane binarne.</span><span class="sxs-lookup"><span data-stu-id="8d830-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="8d830-107">Aby jawnie kontrolować to zachowanie, ustaw <code>aspnet:AllowRelaxedUnicodeDecoding</code> atrybutu [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) elementu <code>true</code> Aby włączyć starsze zachowanie lub <code>false</code> włączyć bieżące zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8d830-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>|
|<span data-ttu-id="8d830-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="8d830-108">Scope</span></span>|<span data-ttu-id="8d830-109">Mały</span><span class="sxs-lookup"><span data-stu-id="8d830-109">Minor</span></span>|
|<span data-ttu-id="8d830-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="8d830-110">Version</span></span>|<span data-ttu-id="8d830-111">4.5</span><span class="sxs-lookup"><span data-stu-id="8d830-111">4.5</span></span>|
|<span data-ttu-id="8d830-112">Typ</span><span class="sxs-lookup"><span data-stu-id="8d830-112">Type</span></span>|<span data-ttu-id="8d830-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8d830-113">Runtime</span></span>|
|<span data-ttu-id="8d830-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8d830-114">Affected APIs</span></span>|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
