---
ms.openlocfilehash: d5768a0c25bcd0880cbffde9e57ca9fe7a81cf06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665714"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="730f2-101">.NET, COM pomyślnie kieruje parametrów ByRef SafeArray zdarzeń</span><span class="sxs-lookup"><span data-stu-id="730f2-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="730f2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="730f2-102">Details</span></span>|<span data-ttu-id="730f2-103">.NET Framework 4.7.2 i wcześniejszych wersjach, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametrem w zdarzenia modelu COM może zakończyć się niepowodzeniem do organizowania powrót do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="730f2-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="730f2-104">Dzięki tej zmianie [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) teraz jest skierowany pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="730f2-104">With this change the [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="730f2-105">[x] quirked</span><span class="sxs-lookup"><span data-stu-id="730f2-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="730f2-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="730f2-106">Suggestion</span></span>|<span data-ttu-id="730f2-107">Jeśli poprawnie kierowania parametrów ByRef SafeArray zdarzeń COM przerywa wykonywanie, możesz wyłączyć ten kod, dodając następujący przełącznik konfiguracji do pliku config aplikacji:</span><span class="sxs-lookup"><span data-stu-id="730f2-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="730f2-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="730f2-108">Scope</span></span>|<span data-ttu-id="730f2-109">Mały</span><span class="sxs-lookup"><span data-stu-id="730f2-109">Minor</span></span>|
|<span data-ttu-id="730f2-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="730f2-110">Version</span></span>|<span data-ttu-id="730f2-111">4.8</span><span class="sxs-lookup"><span data-stu-id="730f2-111">4.8</span></span>|
|<span data-ttu-id="730f2-112">Typ</span><span class="sxs-lookup"><span data-stu-id="730f2-112">Type</span></span>|<span data-ttu-id="730f2-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="730f2-113">Runtime</span></span>|
