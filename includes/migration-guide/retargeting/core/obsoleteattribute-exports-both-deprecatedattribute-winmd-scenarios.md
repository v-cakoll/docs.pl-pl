---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616118"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="f7e4f-101">ObsoleteAttributee eksporty jako ObsoleteAttribute i DeprecatedAttribute w scenariuszach WinMD</span><span class="sxs-lookup"><span data-stu-id="f7e4f-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="f7e4f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f7e4f-102">Details</span></span>

<span data-ttu-id="f7e4f-103">Podczas tworzenia biblioteki metadanych systemu Windows (plik. winmd) ten <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybut jest eksportowany zarówno jako, jak <xref:System.ObsoleteAttribute?displayProperty=fullName> i [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span><span class="sxs-lookup"><span data-stu-id="f7e4f-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7e4f-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f7e4f-104">Suggestion</span></span>

<span data-ttu-id="f7e4f-105">Ponowna kompilacja istniejącego kodu źródłowego korzystającego z <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutu może generować ostrzeżenia podczas korzystania z tego kodu z C++/CX lub JavaScript. nie zaleca się stosowania programów <xref:System.ObsoleteAttribute?displayProperty=fullName> i [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) do kodu w zarządzanych zestawach. może to spowodować wyświetlenie ostrzeżeń dotyczących kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f7e4f-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>

| <span data-ttu-id="f7e4f-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f7e4f-106">Name</span></span>    | <span data-ttu-id="f7e4f-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="f7e4f-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7e4f-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="f7e4f-108">Scope</span></span>   | <span data-ttu-id="f7e4f-109">Brzeg</span><span class="sxs-lookup"><span data-stu-id="f7e4f-109">Edge</span></span>        |
| <span data-ttu-id="f7e4f-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="f7e4f-110">Version</span></span> | <span data-ttu-id="f7e4f-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f7e4f-111">4.5.1</span></span>       |
| <span data-ttu-id="f7e4f-112">Typ</span><span class="sxs-lookup"><span data-stu-id="f7e4f-112">Type</span></span>    | <span data-ttu-id="f7e4f-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f7e4f-113">Retargeting</span></span> |
