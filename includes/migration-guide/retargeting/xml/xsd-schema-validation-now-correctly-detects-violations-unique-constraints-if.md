---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615726"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="481c0-101">Sprawdzanie poprawności schematu XSD teraz prawidłowo wykrywa naruszenia unikatowych ograniczeń, jeśli są używane klucze złożone, a jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="481c0-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="481c0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="481c0-102">Details</span></span>

<span data-ttu-id="481c0-103">Wersje .NET Framework wcześniejsze niż 4,6 miały usterkę, która spowodowała, że Walidacja XSD nie wykryła unikatowych ograniczeń dla kluczy złożonych, jeśli jeden z kluczy był pusty.</span><span class="sxs-lookup"><span data-stu-id="481c0-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="481c0-104">W .NET Framework 4,6 ten problem został rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="481c0-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="481c0-105">Spowoduje to dokładniejsze sprawdzenie poprawności, ale może także spowodować, że niektóre XML nie będą sprawdzać, które wcześniej byłyby.</span><span class="sxs-lookup"><span data-stu-id="481c0-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="481c0-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="481c0-106">Suggestion</span></span>

<span data-ttu-id="481c0-107">W przypadku konieczności walidacji .NET Framework 4,0, sprawdzanie poprawności aplikacji może wskazywać na wersję 4,5 (lub wcześniejszą) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="481c0-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="481c0-108">Po przekierowaniu do .NET Framework 4,6, należy jednak przeprowadzić przegląd kodu, aby upewnić się, że nie można zweryfikować zduplikowanych kluczy złożonych (zgodnie z opisem w opisie tego problemu).</span><span class="sxs-lookup"><span data-stu-id="481c0-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="481c0-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="481c0-109">Name</span></span>    | <span data-ttu-id="481c0-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="481c0-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="481c0-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="481c0-111">Scope</span></span>   | <span data-ttu-id="481c0-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="481c0-112">Edge</span></span>        |
| <span data-ttu-id="481c0-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="481c0-113">Version</span></span> | <span data-ttu-id="481c0-114">4.6</span><span class="sxs-lookup"><span data-stu-id="481c0-114">4.6</span></span>         |
| <span data-ttu-id="481c0-115">Typ</span><span class="sxs-lookup"><span data-stu-id="481c0-115">Type</span></span>    | <span data-ttu-id="481c0-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="481c0-116">Retargeting</span></span> |
