---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440279"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="9239e-101">.NET COM pomyślnie marszałków ByRef SafeArray parametry na zdarzenia</span><span class="sxs-lookup"><span data-stu-id="9239e-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9239e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9239e-102">Details</span></span>|<span data-ttu-id="9239e-103">W .NET Framework 4.7.2 i wcześniejszych wersjach ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru w przypadku COM nie można zorganizować z powrotem do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="9239e-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="9239e-104">Dzięki tej zmianie [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) jest teraz kierowane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9239e-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="9239e-105">[ x ] Dziwaczne</span><span class="sxs-lookup"><span data-stu-id="9239e-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="9239e-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="9239e-106">Suggestion</span></span>|<span data-ttu-id="9239e-107">Jeśli poprawnie kierowanie ByRef SafeArray parametry na zdarzenia COM przerywa wykonywanie, można wyłączyć ten kod, dodając następujący przełącznik konfiguracji do konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9239e-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9239e-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="9239e-108">Scope</span></span>|<span data-ttu-id="9239e-109">Mały</span><span class="sxs-lookup"><span data-stu-id="9239e-109">Minor</span></span>|
|<span data-ttu-id="9239e-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="9239e-110">Version</span></span>|<span data-ttu-id="9239e-111">4.8</span><span class="sxs-lookup"><span data-stu-id="9239e-111">4.8</span></span>|
|<span data-ttu-id="9239e-112">Typ</span><span class="sxs-lookup"><span data-stu-id="9239e-112">Type</span></span>|<span data-ttu-id="9239e-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9239e-113">Runtime</span></span>|
