---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091712"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="c8ca2-101">EncoderParameter ctor jest przestarzała</span><span class="sxs-lookup"><span data-stu-id="c8ca2-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c8ca2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c8ca2-102">Details</span></span>|<span data-ttu-id="c8ca2-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor jest obecnie przestarzała i będzie powodować ostrzeżenia kompilacji, jeśli używane.</span><span class="sxs-lookup"><span data-stu-id="c8ca2-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="c8ca2-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c8ca2-104">Suggestion</span></span>|<span data-ttu-id="c8ca2-105">Mimo że <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor będą nadal działać, następujący Konstruktor należy użyć w celu uniknięcia ostrzeżeń kompilacji przestarzałe podczas ponownego kompilowania kodu za pomocą narzędzi programu .NET Framework 4.5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="c8ca2-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="c8ca2-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="c8ca2-106">Scope</span></span>|<span data-ttu-id="c8ca2-107">Mały</span><span class="sxs-lookup"><span data-stu-id="c8ca2-107">Minor</span></span>|
|<span data-ttu-id="c8ca2-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="c8ca2-108">Version</span></span>|<span data-ttu-id="c8ca2-109">4.5</span><span class="sxs-lookup"><span data-stu-id="c8ca2-109">4.5</span></span>|
|<span data-ttu-id="c8ca2-110">Typ</span><span class="sxs-lookup"><span data-stu-id="c8ca2-110">Type</span></span>|<span data-ttu-id="c8ca2-111">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="c8ca2-111">Retargeting</span></span>|
|<span data-ttu-id="c8ca2-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c8ca2-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
