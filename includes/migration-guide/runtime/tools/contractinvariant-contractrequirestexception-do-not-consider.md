---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621346"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="7f97e-101">Contract. Invariant lub Contract. wymaga, \<TException> aby nie brać pod uwagę ciągu. IsNullOrEmpty jako czysty</span><span class="sxs-lookup"><span data-stu-id="7f97e-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="7f97e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7f97e-102">Details</span></span>

<span data-ttu-id="7f97e-103">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.6.1, jeśli kontrakt niezmienny dla <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> lub kontrakt warunku wstępnego dla <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> wywołania <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody, nastąpi emituje Ostrzeżenie kompilatora CC1036: &quot; wykryto wywołanie metody "System. String. IsNullOrWhteSpace (System. String)" bez [czysty] w metodzie. &quot; Jest to ostrzeżenie kompilatora, a nie błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7f97e-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7f97e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7f97e-104">Suggestion</span></span>

<span data-ttu-id="7f97e-105">To zachowanie zostało opisane w [#339 problemu](https://github.com/Microsoft/CodeContracts/issues/339)w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="7f97e-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="7f97e-106">Aby wyeliminować to ostrzeżenie, można pobrać i skompilować zaktualizowaną wersję kodu źródłowego dla narzędzia kontrakty kodu z usługi [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="7f97e-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="7f97e-107">Informacje na temat pobierania znajdują się u dołu strony.</span><span class="sxs-lookup"><span data-stu-id="7f97e-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="7f97e-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7f97e-108">Name</span></span>    | <span data-ttu-id="7f97e-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="7f97e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7f97e-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="7f97e-110">Scope</span></span>   |<span data-ttu-id="7f97e-111">Mały</span><span class="sxs-lookup"><span data-stu-id="7f97e-111">Minor</span></span>|
|<span data-ttu-id="7f97e-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="7f97e-112">Version</span></span>|<span data-ttu-id="7f97e-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="7f97e-113">4.6.1</span></span>|
|<span data-ttu-id="7f97e-114">Typ</span><span class="sxs-lookup"><span data-stu-id="7f97e-114">Type</span></span>|<span data-ttu-id="7f97e-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7f97e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f97e-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7f97e-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
