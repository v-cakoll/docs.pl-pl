---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620258"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="dae09-101">Marshal. SizeOf i Marshaling. PtrToStructure overloads Break Dynamic Code</span><span class="sxs-lookup"><span data-stu-id="dae09-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="dae09-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="dae09-102">Details</span></span>

<span data-ttu-id="dae09-103">Począwszy od .NET Framework 4.5.1, dynamiczne powiązanie z metodami,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> lub <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> , (za pomocą programu Windows PowerShell, IronPython lub dynamicznego słowa kluczowego C#, na przykład) może spowodować, <code>MethodInvocationExceptions</code> że dodano nowe przeciążenia tych metod, które mogą być niejednoznaczne dla aparatów obsługi skryptów.</span><span class="sxs-lookup"><span data-stu-id="dae09-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dae09-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="dae09-104">Suggestion</span></span>

<span data-ttu-id="dae09-105">Aktualizuj skrypty, aby jasno wskazać, które Przeciążenie powinno być używane.</span><span class="sxs-lookup"><span data-stu-id="dae09-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="dae09-106">Można to zrobić zazwyczaj przez jawne rzutowanie parametrów typu metody na <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="dae09-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="dae09-107">Zobacz [ten link](https://support.microsoft.com/kb/2909958/) , aby uzyskać szczegółowe informacje i przykłady obejścia problemu.</span><span class="sxs-lookup"><span data-stu-id="dae09-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="dae09-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="dae09-108">Name</span></span>    | <span data-ttu-id="dae09-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="dae09-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dae09-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="dae09-110">Scope</span></span>   |<span data-ttu-id="dae09-111">Mały</span><span class="sxs-lookup"><span data-stu-id="dae09-111">Minor</span></span>|
|<span data-ttu-id="dae09-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="dae09-112">Version</span></span>|<span data-ttu-id="dae09-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="dae09-113">4.5.1</span></span>|
|<span data-ttu-id="dae09-114">Typ</span><span class="sxs-lookup"><span data-stu-id="dae09-114">Type</span></span>|<span data-ttu-id="dae09-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="dae09-115">Runtime</span></span>|
