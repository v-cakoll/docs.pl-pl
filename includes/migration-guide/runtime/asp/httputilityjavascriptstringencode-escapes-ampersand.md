---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620146"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="23a05-101">HttpUtility. JavaScriptStringEncode — ucieczki</span><span class="sxs-lookup"><span data-stu-id="23a05-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="23a05-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="23a05-102">Details</span></span>

<span data-ttu-id="23a05-103">Począwszy od .NET Framework 4,5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> wyprowadza znak handlowego "i" ( &amp; ).</span><span class="sxs-lookup"><span data-stu-id="23a05-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="23a05-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="23a05-104">Suggestion</span></span>

<span data-ttu-id="23a05-105">Jeśli aplikacja zależy od poprzedniego zachowania tej metody, można dodać ustawienie ASPNET: JavaScriptDoNotEncodeAmpersand do [elementu appSettings ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="23a05-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="23a05-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="23a05-106">Name</span></span>    | <span data-ttu-id="23a05-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="23a05-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="23a05-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="23a05-108">Scope</span></span>   |<span data-ttu-id="23a05-109">Mały</span><span class="sxs-lookup"><span data-stu-id="23a05-109">Minor</span></span>|
|<span data-ttu-id="23a05-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="23a05-110">Version</span></span>|<span data-ttu-id="23a05-111">4.5</span><span class="sxs-lookup"><span data-stu-id="23a05-111">4.5</span></span>|
|<span data-ttu-id="23a05-112">Typ</span><span class="sxs-lookup"><span data-stu-id="23a05-112">Type</span></span>|<span data-ttu-id="23a05-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="23a05-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23a05-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="23a05-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
