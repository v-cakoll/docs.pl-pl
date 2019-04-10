---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235708"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="46f06-101">HttpUtility.JavaScriptStringEncode specjalne handlowe "i"</span><span class="sxs-lookup"><span data-stu-id="46f06-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

|   |   |
|---|---|
|<span data-ttu-id="46f06-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="46f06-102">Details</span></span>|<span data-ttu-id="46f06-103">Począwszy od programu .NET Framework 4.5 <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> specjalne handlowe "i" (&amp;) znaków.</span><span class="sxs-lookup"><span data-stu-id="46f06-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> escapes the ampersand (&amp;) character.</span></span>|
|<span data-ttu-id="46f06-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="46f06-104">Suggestion</span></span>|<span data-ttu-id="46f06-105">Jeśli Twoja aplikacja zależy od poprzedniego zachowania tej metody, można dodać ustawienie ASPNET: javascriptdonotencodeampersand [elementu appSettings środowiska ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="46f06-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>|
|<span data-ttu-id="46f06-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="46f06-106">Scope</span></span>|<span data-ttu-id="46f06-107">Mały</span><span class="sxs-lookup"><span data-stu-id="46f06-107">Minor</span></span>|
|<span data-ttu-id="46f06-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="46f06-108">Version</span></span>|<span data-ttu-id="46f06-109">4.5</span><span class="sxs-lookup"><span data-stu-id="46f06-109">4.5</span></span>|
|<span data-ttu-id="46f06-110">Typ</span><span class="sxs-lookup"><span data-stu-id="46f06-110">Type</span></span>|<span data-ttu-id="46f06-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="46f06-111">Runtime</span></span>|
|<span data-ttu-id="46f06-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="46f06-112">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
