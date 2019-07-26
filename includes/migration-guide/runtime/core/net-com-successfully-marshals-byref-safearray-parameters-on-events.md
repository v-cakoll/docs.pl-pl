---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440279"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="79626-101">Platforma .NET COM pomyślnie organizowana parametry ByRef SafeArray dla zdarzeń</span><span class="sxs-lookup"><span data-stu-id="79626-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="79626-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="79626-102">Details</span></span>|<span data-ttu-id="79626-103">W .NET Framework 4.7.2 i starszych wersjach parametr ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) dla zdarzenia com nie będzie mógł zostać przekierowany z powrotem do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="79626-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="79626-104">Po zmianie tej zmiany element [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) zostanie teraz skierowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="79626-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="79626-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="79626-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="79626-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="79626-106">Suggestion</span></span>|<span data-ttu-id="79626-107">Jeśli poprawne kierowanie parametrów ByRef w zdarzeniach COM powoduje przerwanie wykonywania, można wyłączyć ten kod, dodając następujący przełącznik konfiguracji do konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="79626-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="79626-108">Scope</span><span class="sxs-lookup"><span data-stu-id="79626-108">Scope</span></span>|<span data-ttu-id="79626-109">Mały</span><span class="sxs-lookup"><span data-stu-id="79626-109">Minor</span></span>|
|<span data-ttu-id="79626-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="79626-110">Version</span></span>|<span data-ttu-id="79626-111">4.8</span><span class="sxs-lookup"><span data-stu-id="79626-111">4.8</span></span>|
|<span data-ttu-id="79626-112">Typ</span><span class="sxs-lookup"><span data-stu-id="79626-112">Type</span></span>|<span data-ttu-id="79626-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="79626-113">Runtime</span></span>|
