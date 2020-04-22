---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021658"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="feb91-101">FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko init</span><span class="sxs-lookup"><span data-stu-id="feb91-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="feb91-102">Począwszy od .NET Core 3.0, wyjątek jest zgłaszany podczas <xref:System.Reflection.FieldAttributes.InitOnly> próby ustawiania wartości na statycznym polu przez wywołanie <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="feb91-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="feb91-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="feb91-103">Change description</span></span>

<span data-ttu-id="feb91-104">W programach .NET Framework i wersjach programu .NET Core przed wersją 3.0 można ustawić wartość pola statycznego, które <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>jest stałe po jego zainicjowaniu[(odczytanym tylko w języku C#),](~/docs/csharp/language-reference/keywords/readonly.md)wywołując program .</span><span class="sxs-lookup"><span data-stu-id="feb91-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="feb91-105">Jednak ustawienie takiego pola w ten sposób spowodowało nieprzewidywalne zachowanie na podstawie struktury docelowej i ustawień optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="feb91-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="feb91-106">W .NET Core 3.0 i nowszych wersjach, po wywołaniu <xref:System.Reflection.FieldInfo.SetValue%2A> na statyczne, <xref:System.Reflection.FieldAttributes.InitOnly> pole, <xref:System.FieldAccessException?displayProperty=nameWithType> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb91-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="feb91-107">Pole <xref:System.Reflection.FieldAttributes.InitOnly> jest takie, które można ustawić tylko w momencie jego deklarowania lub w konstruktorze dla klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="feb91-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="feb91-108">Innymi słowy, jest stała po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="feb91-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="feb91-109">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="feb91-109">Version introduced</span></span>

<span data-ttu-id="feb91-110">3.0</span><span class="sxs-lookup"><span data-stu-id="feb91-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="feb91-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="feb91-111">Recommended action</span></span>

<span data-ttu-id="feb91-112">Inicjuj <xref:System.Reflection.FieldAttributes.InitOnly> statyczne pola w konstruktorze statycznym.</span><span class="sxs-lookup"><span data-stu-id="feb91-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="feb91-113">Dotyczy to zarówno typów dynamicznych, jak i niedynamikowych.</span><span class="sxs-lookup"><span data-stu-id="feb91-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="feb91-114">Alternatywnie można usunąć <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> atrybut z pola, a <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>następnie wywołać .</span><span class="sxs-lookup"><span data-stu-id="feb91-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="feb91-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="feb91-115">Category</span></span>

<span data-ttu-id="feb91-116">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="feb91-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="feb91-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="feb91-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
