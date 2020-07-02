---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617302"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="5858f-101">EncoderParameter ctor jest przestarzały</span><span class="sxs-lookup"><span data-stu-id="5858f-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="5858f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="5858f-102">Details</span></span>

<span data-ttu-id="5858f-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor jest teraz przestarzały i wprowadzi ostrzeżenia kompilacji, jeśli są używane.</span><span class="sxs-lookup"><span data-stu-id="5858f-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5858f-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="5858f-104">Suggestion</span></span>

<span data-ttu-id="5858f-105">Mimo że <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor będzie nadal działać, należy zamiast tego użyć następującego konstruktora, aby uniknąć przestarzałych ostrzeżeń kompilacji podczas ponownego kompilowania kodu za pomocą narzędzi .NET Framework 4,5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)> .</span><span class="sxs-lookup"><span data-stu-id="5858f-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="5858f-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5858f-106">Name</span></span>    | <span data-ttu-id="5858f-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="5858f-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5858f-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="5858f-108">Scope</span></span>   | <span data-ttu-id="5858f-109">Mały</span><span class="sxs-lookup"><span data-stu-id="5858f-109">Minor</span></span>       |
| <span data-ttu-id="5858f-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="5858f-110">Version</span></span> | <span data-ttu-id="5858f-111">4.5</span><span class="sxs-lookup"><span data-stu-id="5858f-111">4.5</span></span>         |
| <span data-ttu-id="5858f-112">Typ</span><span class="sxs-lookup"><span data-stu-id="5858f-112">Type</span></span>    | <span data-ttu-id="5858f-113">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="5858f-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="5858f-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5858f-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
