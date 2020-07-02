---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616125"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="cfdff-101">Dwukierunkowe powiązanie danych z właściwością niepubliczną metodą ustawiającą nie jest obsługiwane</span><span class="sxs-lookup"><span data-stu-id="cfdff-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="cfdff-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cfdff-102">Details</span></span>

<span data-ttu-id="cfdff-103">Próba utworzenia powiązania danych z właściwością bez publicznej metody ustawiającej nigdy nie była obsługiwanego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="cfdff-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="cfdff-104">Począwszy od .NET Framework 4.5.1, ten scenariusz spowoduje zgłoszenie <xref:System.InvalidOperationException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="cfdff-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="cfdff-105">Należy zauważyć, że ten nowy wyjątek zostanie wygenerowany tylko dla aplikacji, które mają specjalne miejsce dla .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="cfdff-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="cfdff-106">Jeśli aplikacja jest przeznaczona dla .NET Framework 4,5, wywołanie będzie dozwolone.</span><span class="sxs-lookup"><span data-stu-id="cfdff-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="cfdff-107">Jeśli aplikacja nie jest ukierunkowana na określoną wersję .NET Framework, powiązanie będzie traktowane jako jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="cfdff-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cfdff-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cfdff-108">Suggestion</span></span>

<span data-ttu-id="cfdff-109">Aplikacja powinna zostać zaktualizowana w taki sposób, aby korzystała z powiązania jednokierunkowego, albo uwidocznić metodę ustawiającą właściwości publicznie.</span><span class="sxs-lookup"><span data-stu-id="cfdff-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="cfdff-110">Alternatywnie, celem .NET Framework 4,5 spowoduje, że aplikacja będzie mieć stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="cfdff-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="cfdff-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cfdff-111">Name</span></span>    | <span data-ttu-id="cfdff-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="cfdff-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cfdff-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="cfdff-113">Scope</span></span>   | <span data-ttu-id="cfdff-114">Mały</span><span class="sxs-lookup"><span data-stu-id="cfdff-114">Minor</span></span>       |
| <span data-ttu-id="cfdff-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="cfdff-115">Version</span></span> | <span data-ttu-id="cfdff-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="cfdff-116">4.5.1</span></span>       |
| <span data-ttu-id="cfdff-117">Typ</span><span class="sxs-lookup"><span data-stu-id="cfdff-117">Type</span></span>    | <span data-ttu-id="cfdff-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="cfdff-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cfdff-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cfdff-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
