---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614819"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a><span data-ttu-id="8bb70-101">Niepoprawna implementacja MemberDescriptor. Equals</span><span class="sxs-lookup"><span data-stu-id="8bb70-101">Incorrect implementation of MemberDescriptor.Equals</span></span>

#### <a name="details"></a><span data-ttu-id="8bb70-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8bb70-102">Details</span></span>

<span data-ttu-id="8bb70-103">Oryginalna implementacja <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody porównuje dwie różne właściwości ciągu z obiektów, które są porównywane: Nazwa kategorii i ciąg opisu.</span><span class="sxs-lookup"><span data-stu-id="8bb70-103">The original implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method compares two different string properties from the objects being compared: the category name and the description string.</span></span> <span data-ttu-id="8bb70-104">Poprawka polega na poprawieniu <xref:System.ComponentModel.MemberDescriptor.Category> pierwszego obiektu do <xref:System.ComponentModel.MemberDescriptor.Category> drugiego, a <xref:System.ComponentModel.MemberDescriptor.Description> pierwszy do <xref:System.ComponentModel.MemberDescriptor.Description> drugiego w drugim.</span><span class="sxs-lookup"><span data-stu-id="8bb70-104">The fix is to compare the <xref:System.ComponentModel.MemberDescriptor.Category> of the first object to the <xref:System.ComponentModel.MemberDescriptor.Category> of the second one, and the <xref:System.ComponentModel.MemberDescriptor.Description> of the first to the <xref:System.ComponentModel.MemberDescriptor.Description> of the second.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8bb70-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8bb70-105">Suggestion</span></span>

<span data-ttu-id="8bb70-106">Jeśli aplikacja jest zależna od <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> czasem `false` , gdy deskryptory są równoważne, a użytkownik jest ukierunkowany na .NET Framework 4.6.2 lub nowszy, masz kilka opcji:</span><span class="sxs-lookup"><span data-stu-id="8bb70-106">If your application depends on <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> sometimes returning `false` when descriptors are equivalent, and you are targeting the .NET Framework 4.6.2 or later, you have several options:</span></span>

- <span data-ttu-id="8bb70-107">Wprowadź zmiany w kodzie, aby <xref:System.ComponentModel.MemberDescriptor.Category> porównać <xref:System.ComponentModel.MemberDescriptor.Description> pola i ręcznie oprócz wywoływania <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8bb70-107">Make code changes to compare the <xref:System.ComponentModel.MemberDescriptor.Category> and <xref:System.ComponentModel.MemberDescriptor.Description> fields manually in addition to calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="8bb70-108">Zrezygnuj z tej zmiany, dodając następującą wartość do pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="8bb70-108">Opt out of this change by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

<span data-ttu-id="8bb70-109">Jeśli aplikacja jest przeznaczona .NET Framework 4.6.1 lub wcześniejsza i jest uruchomiona na .NET Framework 4.6.2 lub nowszej i chcesz, aby ta zmiana została włączona, można ustawić przełącznik zgodności, `false` dodając następującą wartość do pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="8bb70-109">If your application targets .NET Framework 4.6.1 or earlier and is running on the .NET Framework 4.6.2 or later and you want this change enabled, you can set the compatibility switch to `false` by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| <span data-ttu-id="8bb70-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8bb70-110">Name</span></span>    | <span data-ttu-id="8bb70-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="8bb70-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8bb70-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="8bb70-112">Scope</span></span>   | <span data-ttu-id="8bb70-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="8bb70-113">Edge</span></span>        |
| <span data-ttu-id="8bb70-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="8bb70-114">Version</span></span> | <span data-ttu-id="8bb70-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8bb70-115">4.6.2</span></span>       |
| <span data-ttu-id="8bb70-116">Typ</span><span class="sxs-lookup"><span data-stu-id="8bb70-116">Type</span></span>    | <span data-ttu-id="8bb70-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="8bb70-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8bb70-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8bb70-118">Affected APIs</span></span>

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
