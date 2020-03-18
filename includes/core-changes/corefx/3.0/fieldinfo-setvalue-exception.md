---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449566"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="64194-101">FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko do init</span><span class="sxs-lookup"><span data-stu-id="64194-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="64194-102">Począwszy od .NET Core 3.0, wyjątek jest generowany podczas próby ustawienie wartości na statyczne pole, <xref:System.Reflection.FieldAttributes.InitOnly> wywołując <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="64194-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64194-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="64194-103">Change description</span></span>

<span data-ttu-id="64194-104">W platformie .NET Framework i wersjach programu .NET Core przed wersją 3.0 można ustawić wartość stałego pola statycznego <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>po jego zainicjowaniu[(tylko do odczytu w języku C#),](~/docs/csharp/language-reference/keywords/readonly.md)wywołując .</span><span class="sxs-lookup"><span data-stu-id="64194-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="64194-105">Jednak ustawienie takiego pola w ten sposób spowodowało nieprzewidywalne zachowanie na podstawie docelowej struktury i ustawień optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="64194-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="64194-106">W wersji .NET Core 3.0 i <xref:System.Reflection.FieldInfo.SetValue%2A> nowszych, podczas <xref:System.FieldAccessException?displayProperty=nameWithType> wywoływania statycznego pola, <xref:System.Reflection.FieldAttributes.InitOnly> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="64194-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="64194-107">Pole <xref:System.Reflection.FieldAttributes.InitOnly> to pole, które można ustawić tylko w momencie, gdy jest zadeklarowany lub w konstruktorze dla klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="64194-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="64194-108">Innymi słowy, jest stała po jego zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="64194-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64194-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="64194-109">Version introduced</span></span>

<span data-ttu-id="64194-110">3.0</span><span class="sxs-lookup"><span data-stu-id="64194-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64194-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="64194-111">Recommended action</span></span>

<span data-ttu-id="64194-112">Inicjuj <xref:System.Reflection.FieldAttributes.InitOnly> statyczne pola w konstruktorze statycznym.</span><span class="sxs-lookup"><span data-stu-id="64194-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="64194-113">Dotyczy to zarówno typów dynamicznych, jak i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="64194-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="64194-114">Alternatywnie można usunąć <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atrybut z pola, a <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>następnie wywołać .</span><span class="sxs-lookup"><span data-stu-id="64194-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="64194-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="64194-115">Category</span></span>

<span data-ttu-id="64194-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="64194-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64194-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="64194-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
