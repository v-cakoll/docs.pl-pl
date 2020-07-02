---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620408"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="ed2e1-101">Funkcja WF serializować wyrażenia. literały &lt; T &gt; datetimes są teraz inaczej (dzieli Niestandardowe analizatory języka XAML)</span><span class="sxs-lookup"><span data-stu-id="ed2e1-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="ed2e1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ed2e1-102">Details</span></span>

<span data-ttu-id="ed2e1-103">Skojarzony <xref:System.Windows.Markup.ValueSerializer> obiekt spowoduje przekonwertowanie <xref:System.DateTime?displayProperty=fullName> obiektu lub, <xref:System.DateTimeOffset?displayProperty=fullName> którego sekunda i <xref:System.DateTime.Millisecond?displayProperty=fullName> składniki są inne niż zero i (dla <xref:System.DateTime?displayProperty=fullName> wartości), których <xref:System.DateTime.Kind> Właściwość nie została określona jako składnia elementu właściwości zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="ed2e1-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="ed2e1-104">Ta zmiana umożliwia <xref:System.DateTime?displayProperty=fullName> i <xref:System.DateTimeOffset?displayProperty=fullName> wartości, które mają być okrężne.</span><span class="sxs-lookup"><span data-stu-id="ed2e1-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="ed2e1-105">Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ed2e1-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed2e1-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ed2e1-106">Suggestion</span></span>

<span data-ttu-id="ed2e1-107">Ta zmiana umożliwia <xref:System.DateTime?displayProperty=fullName> i <xref:System.DateTimeOffset?displayProperty=fullName> wartości, które mają być okrężne.</span><span class="sxs-lookup"><span data-stu-id="ed2e1-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="ed2e1-108">Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ed2e1-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="ed2e1-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ed2e1-109">Name</span></span>    | <span data-ttu-id="ed2e1-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="ed2e1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed2e1-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="ed2e1-111">Scope</span></span>   |<span data-ttu-id="ed2e1-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="ed2e1-112">Edge</span></span>|
|<span data-ttu-id="ed2e1-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="ed2e1-113">Version</span></span>|<span data-ttu-id="ed2e1-114">4.5</span><span class="sxs-lookup"><span data-stu-id="ed2e1-114">4.5</span></span>|
|<span data-ttu-id="ed2e1-115">Typ</span><span class="sxs-lookup"><span data-stu-id="ed2e1-115">Type</span></span>|<span data-ttu-id="ed2e1-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ed2e1-116">Runtime</span></span>|
