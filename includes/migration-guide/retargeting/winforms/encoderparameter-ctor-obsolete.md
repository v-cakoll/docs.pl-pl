---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234803"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="49259-101">EncoderParameter ctor jest przestarzała</span><span class="sxs-lookup"><span data-stu-id="49259-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="49259-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="49259-102">Details</span></span>|<span data-ttu-id="49259-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor jest obecnie przestarzała i będzie powodować ostrzeżenia kompilacji, jeśli używane.</span><span class="sxs-lookup"><span data-stu-id="49259-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="49259-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="49259-104">Suggestion</span></span>|<span data-ttu-id="49259-105">Mimo że <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor będą nadal działać, następujący Konstruktor należy użyć w celu uniknięcia ostrzeżeń kompilacji przestarzałe podczas ponownego kompilowania kodu za pomocą narzędzi programu .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="49259-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="49259-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="49259-106">Scope</span></span>|<span data-ttu-id="49259-107">Mały</span><span class="sxs-lookup"><span data-stu-id="49259-107">Minor</span></span>|
|<span data-ttu-id="49259-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="49259-108">Version</span></span>|<span data-ttu-id="49259-109">4.5</span><span class="sxs-lookup"><span data-stu-id="49259-109">4.5</span></span>|
|<span data-ttu-id="49259-110">Typ</span><span class="sxs-lookup"><span data-stu-id="49259-110">Type</span></span>|<span data-ttu-id="49259-111">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="49259-111">Retargeting</span></span>|
|<span data-ttu-id="49259-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="49259-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
