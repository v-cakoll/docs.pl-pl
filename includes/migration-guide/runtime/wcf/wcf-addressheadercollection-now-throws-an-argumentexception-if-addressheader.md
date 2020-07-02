---
ms.openlocfilehash: d29be721b50d1c93723b325774a06e86f77dbebf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621226"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="1c95d-101">Funkcja WCF AddressHeaderCollection teraz generuje ArgumentException, jeśli element addressHeader ma wartość null</span><span class="sxs-lookup"><span data-stu-id="1c95d-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="1c95d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1c95d-102">Details</span></span>

<span data-ttu-id="1c95d-103">Rozpoczynając od .NET Framework 4.7.1, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Konstruktor zgłasza, <xref:System.ArgumentException> Jeśli jeden z elementów jest <code>null</code> .</span><span class="sxs-lookup"><span data-stu-id="1c95d-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is <code>null</code>.</span></span> <span data-ttu-id="1c95d-104">W .NET Framework 4,7 i wcześniejszych wersjach nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1c95d-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1c95d-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1c95d-105">Suggestion</span></span>

<span data-ttu-id="1c95d-106">Jeśli wystąpią problemy ze zgodnością z tą zmianą w .NET Framework 4.7.1 lub nowszej wersji, możesz zrezygnować z niej, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config::</span><span class="sxs-lookup"><span data-stu-id="1c95d-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config file::</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1c95d-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1c95d-107">Name</span></span>    | <span data-ttu-id="1c95d-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="1c95d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1c95d-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="1c95d-109">Scope</span></span>   |<span data-ttu-id="1c95d-110">Mały</span><span class="sxs-lookup"><span data-stu-id="1c95d-110">Minor</span></span>|
|<span data-ttu-id="1c95d-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="1c95d-111">Version</span></span>|<span data-ttu-id="1c95d-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="1c95d-112">4.7.1</span></span>|
|<span data-ttu-id="1c95d-113">Typ</span><span class="sxs-lookup"><span data-stu-id="1c95d-113">Type</span></span>|<span data-ttu-id="1c95d-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1c95d-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c95d-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1c95d-115">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})></li></ul>|
