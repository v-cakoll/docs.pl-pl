---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449566"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="f0e00-101">Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init</span><span class="sxs-lookup"><span data-stu-id="f0e00-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="f0e00-102">Począwszy od platformy .NET Core 3,0, wyjątek jest zgłaszany podczas próby ustawienia wartości w statycznej <xref:System.Reflection.FieldAttributes.InitOnly> polu przez wywołanie <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="f0e00-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f0e00-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="f0e00-103">Change description</span></span>

<span data-ttu-id="f0e00-104">W .NET Framework i wersjach programu .NET Core wcześniejszych niż 3,0, można ustawić wartość pola statycznego, które jest stałe po zainicjowaniu ([ReadOnly in C# ](~/docs/csharp/language-reference/keywords/readonly.md)), wywołując <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="f0e00-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="f0e00-105">Jednak ustawienie takiego pola w ten sposób skutkuje nieprzewidywalnym zachowaniem na podstawie ustawień platformy docelowej i optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="f0e00-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="f0e00-106">W przypadku programu .NET Core 3,0 i jego nowszych wersji, gdy wywołasz <xref:System.Reflection.FieldInfo.SetValue%2A> w statycznej <xref:System.Reflection.FieldAttributes.InitOnly> polu, zostanie zgłoszony wyjątek <xref:System.FieldAccessException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0e00-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="f0e00-107"><xref:System.Reflection.FieldAttributes.InitOnly> pole to takie, które można ustawić tylko w czasie, gdy jest zadeklarowany, lub w konstruktorze dla klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="f0e00-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="f0e00-108">Innymi słowy, jest ona stała po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="f0e00-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f0e00-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f0e00-109">Version introduced</span></span>

<span data-ttu-id="f0e00-110">3.0</span><span class="sxs-lookup"><span data-stu-id="f0e00-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f0e00-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f0e00-111">Recommended action</span></span>

<span data-ttu-id="f0e00-112">Inicjuj statyczne <xref:System.Reflection.FieldAttributes.InitOnly> pól w konstruktorze statycznym.</span><span class="sxs-lookup"><span data-stu-id="f0e00-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="f0e00-113">Dotyczy to zarówno typów dynamicznych, jak i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="f0e00-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="f0e00-114">Alternatywnie możesz usunąć atrybut <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> z pola, a następnie wywołać <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0e00-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="f0e00-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f0e00-115">Category</span></span>

<span data-ttu-id="f0e00-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f0e00-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f0e00-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f0e00-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
