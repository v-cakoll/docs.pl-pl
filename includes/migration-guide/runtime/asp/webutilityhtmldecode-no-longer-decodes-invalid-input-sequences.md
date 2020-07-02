---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620161"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="16e28-101">WebUtility.HtmlDecode nie może już dekodować nieprawidłowych sekwencji wejściowych</span><span class="sxs-lookup"><span data-stu-id="16e28-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="16e28-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="16e28-102">Details</span></span>

<span data-ttu-id="16e28-103">Domyślnie metody dekodowania nie dekodują już nieprawidłowych sekwencji wejściowych na nieprawidłowy ciąg UTF-16.</span><span class="sxs-lookup"><span data-stu-id="16e28-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="16e28-104">Zamiast tego zwracają oryginalne dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="16e28-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="16e28-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="16e28-105">Suggestion</span></span>

<span data-ttu-id="16e28-106">Zmiana w danych wyjściowych dekodera powinna mieć znaczenie tylko wtedy, gdy w ciągach zamiast danych UTF-16 są przechowywane dane binarne.</span><span class="sxs-lookup"><span data-stu-id="16e28-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="16e28-107">Aby jawnie kontrolować to zachowanie, ustaw <code>aspnet:AllowRelaxedUnicodeDecoding</code> atrybut elementu [AppSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) na <code>true</code> , aby włączyć starsze zachowanie lub aby <code>false</code> włączyć bieżące zachowanie.</span><span class="sxs-lookup"><span data-stu-id="16e28-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="16e28-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="16e28-108">Name</span></span>    | <span data-ttu-id="16e28-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="16e28-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="16e28-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="16e28-110">Scope</span></span>   |<span data-ttu-id="16e28-111">Mały</span><span class="sxs-lookup"><span data-stu-id="16e28-111">Minor</span></span>|
|<span data-ttu-id="16e28-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="16e28-112">Version</span></span>|<span data-ttu-id="16e28-113">4.5</span><span class="sxs-lookup"><span data-stu-id="16e28-113">4.5</span></span>|
|<span data-ttu-id="16e28-114">Typ</span><span class="sxs-lookup"><span data-stu-id="16e28-114">Type</span></span>|<span data-ttu-id="16e28-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="16e28-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="16e28-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="16e28-116">Affected APIs</span></span>

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
