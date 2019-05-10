---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65199309"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="d57f6-101">.NET, COM pomyślnie kieruje parametrów ByRef SafeArray zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d57f6-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d57f6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d57f6-102">Details</span></span>|<span data-ttu-id="d57f6-103">.NET Framework 4.7.2 i wcześniejszych wersjach, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametrem w zdarzenia modelu COM może zakończyć się niepowodzeniem do organizowania powrót do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="d57f6-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="d57f6-104">Dzięki tej zmianie [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) teraz jest organizowana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d57f6-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshaled successfully.</span></span><ul><li><span data-ttu-id="d57f6-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="d57f6-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="d57f6-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d57f6-106">Suggestion</span></span>|<span data-ttu-id="d57f6-107">Jeśli poprawnie marshaling parametrów ByRef SafeArray zdarzeń COM przerywa wykonywanie, możesz wyłączyć ten kod, dodając następujący przełącznik konfiguracji do pliku config aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d57f6-107">If properly marshaling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="d57f6-108">Scope</span><span class="sxs-lookup"><span data-stu-id="d57f6-108">Scope</span></span>|<span data-ttu-id="d57f6-109">Mały</span><span class="sxs-lookup"><span data-stu-id="d57f6-109">Minor</span></span>|
|<span data-ttu-id="d57f6-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="d57f6-110">Version</span></span>|<span data-ttu-id="d57f6-111">4.8</span><span class="sxs-lookup"><span data-stu-id="d57f6-111">4.8</span></span>|
|<span data-ttu-id="d57f6-112">Typ</span><span class="sxs-lookup"><span data-stu-id="d57f6-112">Type</span></span>|<span data-ttu-id="d57f6-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d57f6-113">Runtime</span></span>|
