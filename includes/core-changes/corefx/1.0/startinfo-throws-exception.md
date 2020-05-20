---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420434"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="5271f-101">Proces. element StartInfo zgłasza InvalidOperationException dla procesów, które nie zostały uruchomione</span><span class="sxs-lookup"><span data-stu-id="5271f-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="5271f-102">Odczytywanie <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> właściwości procesów, w których kod nie został uruchomiony, zgłasza <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="5271f-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5271f-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="5271f-103">Change description</span></span>

<span data-ttu-id="5271f-104">W .NET Framework dostęp do <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> właściwości dla procesów, których kod nie został uruchomiony, zwraca fikcyjny <xref:System.Diagnostics.ProcessStartInfo> obiekt.</span><span class="sxs-lookup"><span data-stu-id="5271f-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="5271f-105">Fikcyjny obiekt zawiera wartości domyślne dla wszystkich jego właściwości z wyjątkiem <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .</span><span class="sxs-lookup"><span data-stu-id="5271f-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="5271f-106">Począwszy od platformy .NET Core 1,0, jeśli odczytasz <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> Właściwość dla procesu, który nie został uruchomiony (oznacza to przez wywołanie <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ), <xref:System.InvalidOperationException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="5271f-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5271f-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="5271f-107">Version introduced</span></span>

<span data-ttu-id="5271f-108">1.0</span><span class="sxs-lookup"><span data-stu-id="5271f-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5271f-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="5271f-109">Recommended action</span></span>

<span data-ttu-id="5271f-110">Nie uzyskuj dostępu do <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> właściwości dla procesów, w których kod nie został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5271f-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="5271f-111">Na przykład nie należy odczytywać tej właściwości dla procesów zwracanych przez <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5271f-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="5271f-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="5271f-112">Category</span></span>

<span data-ttu-id="5271f-113">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5271f-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5271f-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5271f-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
